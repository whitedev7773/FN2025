<script lang="ts">
	import DateBox from './remaining_time/DateBox.svelte';

	export let targetDate: Date = new Date('2025-05-29T18:00:00');

	import { onMount } from 'svelte';

	let remainingDays: number;
	let remainingHours: number;
	let remainingMinutes: number;
	let remainingSeconds: number;

	const updateRemainingTime = () => {
		const currentDate = new Date();
		let remainingTime = targetDate.getTime() - currentDate.getTime();

		if (remainingTime < 0) {
			remainingDays = 0;
			remainingHours = 0;
			remainingMinutes = 0;
			remainingSeconds = 0;
			return;
		}

		remainingTime = Math.floor(remainingTime / 1000);

		remainingDays = Math.floor(remainingTime / (60 * 60 * 24));
		remainingTime -= remainingDays * 60 * 60 * 24;

		remainingHours = Math.floor(remainingTime / (60 * 60));
		remainingTime -= remainingHours * 60 * 60;

		remainingMinutes = Math.floor(remainingTime / 60);
		remainingTime -= remainingMinutes * 60;

		remainingSeconds = remainingTime;
	};

	onMount(() => {
		updateRemainingTime();
		const interval = setInterval(updateRemainingTime, 1000);
		return () => clearInterval(interval);
	});
</script>

<div>
	<DateBox label="DAY" display_number={remainingDays} />
	<DateBox label="HOUR" display_number={remainingHours} />
	<DateBox label="MINUTE" display_number={remainingMinutes} />
	<DateBox label="SECOND" display_number={remainingSeconds} />
</div>

<style>
	div {
		padding: 20px;

		display: flex;
		justify-content: center;
		align-items: center;
		gap: 10px;

		border-radius: 20px;
		border: 2px solid #ffffff38;

		user-select: none;
	}
</style>
