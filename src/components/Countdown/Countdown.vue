<template>
	<div class="countdown-container">
		<h1 class="heading">Angel's birthday is in</h1>
		<div class="countdown-cards">
			<countdown-card
				v-for="data in countdownCardsData"
				:key="data.name"
				:cardTitle="data.name"
				:cardCount="data.count"
			/>
		</div>
	</div>
</template>

<script>
import CountdownCard from '../CountdownCard/CountdownCard.vue';
import intervalToDuration from 'date-fns/intervalToDuration';
import isAfter from 'date-fns/isAfter';
import addYears from 'date-fns/addYears';

export default {
	components: { CountdownCard },
	name: 'AppCountdown',
	data() {
		return {
			countdownCardsData: [
				{ name: 'days', count: 0 },
				{ name: 'hours', count: 0 },
				{ name: 'minutes', count: 0 },
				{ name: 'seconds', count: 0 },
			],
			end: this.endDate,
			countdownIntervalId: '',
			countdownHasEnd: isAfter(this.startDate, this.endDate),
			countdownIntervalDuration: 1000,
			intervalDuration: intervalToDuration({
				start: this.startDate,
				end: this.endDate,
			}),
		};
	},
	props: {
		startDate: {
			type: Date,
			required: true,
		},
		endDate: {
			type: Date,
			required: true,
		},
	},
	methods: {
		runInterval: function() {
			this.countdownIntervalId = setInterval(() => {
				this.updateDate();
			}, this.countdownIntervalDuration);
		},
		updateDate: function() {
			if (this.countdownHasEnd) {
				this.end = addYears(this.endDate, 1);

				this.$emit('increaseYear', this.end);
			}

			this.intervalDuration = intervalToDuration({
				start: new Date(),
				end: this.end,
			});

			const currentYear = new Date().getFullYear();

			const daysOfTheYear = this.isLeapYear(currentYear) ? 366 : 365;

			const daysPerMonth = daysOfTheYear / 12;

			const duration = this.intervalDuration;

			const days = Math.floor(duration.days + daysPerMonth * duration.months);

			const remainingDate = {
				days,
				hours: duration.hours,
				minutes: duration.minutes,
				seconds: duration.seconds,
			};

			this.countdownCardsData = this.countdownCardsData.map(item => ({
				name: item.name,
				count: remainingDate[item.name],
			}));

			this.countdownHasEnd = isAfter(new Date(), this.endDate);
		},
		isLeapYear: function(year) {
			return year % 400 === 0 || (year % 100 !== 0 && year % 4 === 0);
		},
	},
	computed: {
		getFormatedDate() {
			return null;
		},
	},
	beforeMount() {
		this.updateDate();
	},
	mounted() {
		this.runInterval();
	},
	destroyed() {
		clearInterval(this.countdownIntervalId);
	},
};
</script>

<style scoped>
.countdown-container {
	align-items: center;
	display: flex;
	flex-direction: column;
	padding: 146px 26px 48px;
	font-size: 16px;
	width: 100%;
	flex: 100%;
}

h1 {
	color: var(--white);
	font-family: var(--ff-red-hat);
	font-size: 16px;
	font-weight: var(--fw-bold);
	letter-spacing: 6px;
	line-height: 1.5;
	margin-bottom: 60px;
	text-align: center;
	text-transform: uppercase;
}

.success-message {
	color: var(--white);
	font-size: 2.4em;
	font-weight: var(--fw-bold);
	text-align: center;
	letter-spacing: 2px;
	text-shadow: 0 4px 4px rgba(255, 255, 255, 0.2);
	margin: auto;
}

.countdown-cards {
	display: grid;
	font-size: 3.3vw;
	grid-template-columns: repeat(4, 5.8em);
	grid-template-rows: 5.5em;
	max-width: 688px;
	place-content: space-between;
	width: 100%;
}

@media screen and (min-width: 768px) {
	.countdown-cards {
		font-size: 2.3vw;
	}
}

@media screen and (min-width: 1280px) {
	.countdown-cards {
		font-size: 26px;
	}

	.success-message {
		font-size: 3.2em;
		max-width: 1140px;
	}
}
</style>
