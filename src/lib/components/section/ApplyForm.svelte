<!-- +page.svelte -->
<script>
	import '$lib/styles/color.css';
	import '$lib/styles/effects.css';
	import Text from '$lib/components/Text.svelte';

	export let id = '';

	let name = '';
	let phone = '';
	let email = '';
	let is_deposited = false; // 입금 내역
	let bank_account = ''; // 은행계좌 정보
	let inflow_selected = ''; // 유입 경로
	let inflow_option = [
		'함수달 인스타그램(@fun_sudal)',
		'다른 인스타그램 채널(@knu_notice 등)',
		'지인 추천',
		'이전 참여 경험',
		'카카오톡',
		'기타'
	];
	let comment = ''; // 원하는 사항
	let agree_to_terms = false; // 개인정보처리 동의
	let agree_to_conduct = false; // 행동강령 동의

	const submitToGoogleForm = async () => {
		const formData = new FormData();
		formData.append('entry.2070974092', name); // name 필드
		formData.append('entry.366638934', email); // email 필드
		formData.append('entry.1165508188', phone); // phone 필드
		formData.append('entry.1108660552', is_deposited ? '예, 입금했습니다' : ''); // is_deposited 필드
		formData.append('entry.1696218478', inflow_selected); // inflow_option 필드
		formData.append('entry.1478399583', comment); // comment 필드
		formData.append('entry.711648269', bank_account); // 은행계좌 정보 필드
		formData.append('entry.383730365', agree_to_terms ? '동의함' : ''); // agree_to_terms 필드
		formData.append('entry.1499024358', agree_to_conduct ? '동의함' : ''); // agree_to_conduct 필드

		try {
			await fetch(
				`https://docs.google.com/forms/d/e/1FAIpQLSc0ilxatCDyqAGMGzYxBhu4SUpsPpugiTanlyqFpimvLCSH5w/formResponse`,
				{
					method: 'POST',
					mode: 'no-cors',
					body: formData
				}
			);
			alert('신청서가 제출되었습니다. 감사합니다!');

			// Reset form fields
			name = '';
			email = '';
			phone = '';
			is_deposited = false;
			bank_account = '';
			inflow_selected = '';
			comment = '';
			agree_to_terms = false;
			agree_to_conduct = false;
		} catch (error) {
			console.error('Error submitting form:', error);
			alert('신청서 제출에 실패했습니다. 다시 시도해주세요.\n계속 반복될 경우 문의해주세요.');
			return;
		}
	};
</script>

<section {id}>
	<Text fontSize="69px" fontWeight="700" mobileFontSize="30px">APPLY</Text>
	<form on:submit|preventDefault={submitToGoogleForm} class="form">
		<div class="form-group">
			<label for="name" class="label">이름 *</label>
			<input
				id="name"
				type="text"
				bind:value={name}
				placeholder="이름을 입력해주세요"
				class="input"
				required
			/>
		</div>

		<div class="form-group">
			<label for="email" class="label">이메일 *</label>
			<input
				id="email"
				type="email"
				bind:value={email}
				placeholder="example@email.com"
				class="input"
				required
			/>
		</div>

		<div class="form-group">
			<label for="phone" class="label">전화번호 *</label>
			<input
				id="phone"
				type="tel"
				bind:value={phone}
				placeholder="- 기호 없이 입력"
				class="input"
				required
			/>
		</div>

		<div class="form-group">
			<label for="inflow" class="label">유입 경로 *</label>
			<select id="inflow" bind:value={inflow_selected} class="select" required>
				<option value="" disabled selected>유입 경로를 선택해주세요</option>
				{#each inflow_option as option}
					<option value={option}>{option}</option>
				{/each}
			</select>
		</div>

		<div class="form-group">
			<label for="comment" class="label">원하는 사항</label>
			<textarea
				id="comment"
				bind:value={comment}
				placeholder="추가로 전달하고 싶은 내용이 있다면 작성해주세요"
				class="textarea"
				rows="4"
			></textarea>
		</div>

		<div class="checkbox-group">
			<div class="description">
				<h2>예약비 입금 안내</h2>
				<p>5,000원은 '예약비'이므로 행사 참여 시 전액 환불 됩니다 (노쇼시 환불 불가)</p>
				<p>토스뱅크 1001-8381-6131 권선우(모임통장)로 5,000원 입금 후 아래에 체크해주세요</p>
				<p>입금자 명은 입금자 성함+전화번호 뒷자리로 수정해주세요 ex) 홍길동1234</p>
				<span>*입금 확인 후 최종 접수됩니다.</span>
			</div>

			<label class="checkbox-label" style="margin-top: 30px">
				<input type="checkbox" bind:checked={is_deposited} class="checkbox" required />
				<span class="checkmark"></span>
				<span class="checkbox-text">예약비 입금을 완료했습니다 *</span>
			</label>

			<div class="form-group" style="margin-top: 40px">
				<label for="bank_account" class="label">환불받으실 은행계좌 *</label>
				<input
					id="bank_account"
					type="text"
					bind:value={bank_account}
					placeholder="홍길동 NH농협 1234567890"
					class="input"
					required
				/>
			</div>
		</div>

		<div class="checkbox-group">
			<div class="description">
				<h2>개인정보 수집 및 이용 안내</h2>
				<p>
					<a href="/policy" target="_blank">개인정보 처리방침</a>을 확인 후 동의해주세요.
				</p>
			</div>

			<label class="checkbox-label required" style="margin-top: 30px">
				<input type="checkbox" bind:checked={agree_to_terms} class="checkbox" required />
				<span class="checkmark"></span>
				<span class="checkbox-text">개인정보 수집 및 이용에 동의합니다 *</span>
			</label>
		</div>

		<div class="checkbox-group">
			<div class="description">
				<h2>행동강령 안내</h2>
				<p>
					<a href="/rule" target="_blank">행동강령</a>을 확인 후 동의해주세요.
				</p>
			</div>
			<label class="checkbox-label required">
				<input type="checkbox" bind:checked={agree_to_conduct} class="checkbox" required />
				<span class="checkmark"></span>
				<span class="checkbox-text">행동강령에 동의합니다 *</span>
			</label>
		</div>
		<button type="submit" class="submit-btn">
			<span>신청서 제출</span>
			<svg
				class="arrow"
				width="20"
				height="20"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M5 12H19M19 12L12 5M19 12L12 19"
					stroke="currentColor"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</button>
	</form>
</section>

<style>
	section {
		width: 100%;
		padding: 100px 0px;
		box-sizing: border-box;

		position: relative;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 70px;

		background-color: var(--navy);
	}

	.form {
		width: 650px;
		display: flex;
		flex-direction: column;
		gap: 40px;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		gap: 6px;
	}

	.description {
		display: flex;
		flex-direction: column;
		gap: 20px;
		margin-bottom: 20px;
	}

	.description p {
		color: rgba(255, 255, 255, 0.75);
	}

	.description span {
		color: rgba(255, 0, 0, 1);
	}

	a {
		color: rgba(255, 255, 255, 0.75);
		text-decoration: underline;
	}

	.label {
		font-size: 0.95rem;
		font-weight: 600;
		color: rgba(255, 255, 255, 0.9);
		margin-left: 2px;
		margin-bottom: 4px;
	}

	.input,
	.select,
	.textarea {
		padding: 16px 20px;
		border: 1px solid rgba(255, 255, 255, 0.15);
		border-radius: 12px;
		background: rgba(255, 255, 255, 0.05);
		color: white;
		font-size: 1rem;
		transition: all 0.3s ease;
		outline: none;
		backdrop-filter: blur(5px);
		vertical-align: middle;
	}

	.input::placeholder,
	.textarea::placeholder {
		color: rgba(255, 255, 255, 0.5);
	}

	.input:focus,
	.select:focus,
	.textarea:focus {
		border-color: rgba(255, 255, 255, 0.4);
		background: rgba(255, 255, 255, 0.08);
		box-shadow: 0 0 0 3px rgba(255, 255, 255, 0.1);
	}

	.select {
		cursor: pointer;
	}

	.select option {
		background: #020a1f;
		color: white;
		padding: 8px;
	}

	.textarea {
		resize: vertical;
		min-height: 100px;
		font-family: inherit;
	}

	.checkbox-group {
		margin: 8px 0;
		padding: 20px;
		border: solid 1px rgba(255, 255, 255, 0.15);
		border-radius: 12px;
	}

	.checkbox-label {
		display: flex;
		align-items: flex-start;
		gap: 12px;
		cursor: pointer;
		line-height: 1.5;
		position: relative;
	}

	.checkbox {
		appearance: none;
		width: 20px;
		height: 20px;
		margin: 0;
		flex-shrink: 0;
		margin-top: 2px;
	}

	.checkmark {
		position: absolute;
		top: 2px;
		left: 0;
		width: 20px;
		height: 20px;
		border: 2px solid rgba(255, 255, 255, 0.3);
		border-radius: 4px;
		background: transparent;
		transition: all 0.3s ease;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.checkmark::after {
		content: '';
		width: 6px;
		height: 10px;
		border: solid white;
		border-width: 0 2px 2px 0;
		transform: rotate(45deg);
		opacity: 0;
		transition: opacity 0.2s ease;
	}

	.checkbox:checked + .checkmark {
		background: rgba(255, 255, 255, 0.2);
		border-color: rgba(255, 255, 255, 0.6);
	}

	.checkbox:checked + .checkmark::after {
		opacity: 1;
	}

	.checkbox-text {
		font-size: 0.95rem;
		color: rgba(255, 255, 255, 0.85);
		user-select: none;
	}

	.submit-btn {
		background: linear-gradient(
			135deg,
			rgba(255, 255, 255, 0.15) 0%,
			rgba(255, 255, 255, 0.05) 100%
		);
		border: 1px solid rgba(255, 255, 255, 0.2);
		color: white;
		padding: 18px 32px;
		border-radius: 12px;
		font-size: 1.1rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 12px;
		margin-top: 16px;
		backdrop-filter: blur(10px);
	}

	.submit-btn:hover {
		background: linear-gradient(
			135deg,
			rgba(255, 255, 255, 0.25) 0%,
			rgba(255, 255, 255, 0.1) 100%
		);
		border-color: rgba(255, 255, 255, 0.3);
		transform: translateY(-2px);
		box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
	}

	.submit-btn:active {
		transform: translateY(0);
	}

	.arrow {
		transition: transform 0.3s ease;
	}

	.submit-btn:hover .arrow {
		transform: translateX(4px);
	}

	/* 모바일 대응 */
	@media (max-width: 768px) {
		.form {
			width: calc(100% - 40px);
			gap: 20px;
		}

		.input,
		.select,
		.textarea {
			padding: 14px 16px;
			font-size: 16px; /* iOS에서 줌 방지 */
		}

		.submit-btn {
			padding: 16px 24px;
			font-size: 1rem;
		}

		.checkbox-label {
			gap: 10px;
		}

		.checkmark {
			width: 18px;
			height: 18px;
		}

		.checkbox {
			width: 18px;
			height: 18px;
		}
	}

	@media (max-width: 480px) {
		.form {
			gap: 18px;
		}
	}
</style>
