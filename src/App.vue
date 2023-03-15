<template>
  <h1>Count all people by their age</h1>
  <h2>Total count: {{ totalCount }}</h2>
  <AttendeeCounter
    v-for="({ text, counter }, index) in attendeeCounters"
    :key="text"
    :text="text"
    :counter="counter"
    @increase="handleIncrease(index)"
    @decrease="handleDecrease(index)"
  />
</template>

<script>
import AttendeeCounter from "./components/AttendeeCounter.vue";

export default {
  name: "App",
  data() {
    return {
      attendeeCounters: [
        {
          text: "5-12 years",
          counter: 0,
        },
        {
          text: "12-18 years",
          counter: 0,
        },
        {
          text: "18-30 years",
          counter: 0,
        },
        {
          text: "30-50 years",
          counter: 0,
        },
      ],
    };
  },
  components: {
    AttendeeCounter,
  },
  computed: {
    totalCount() {
      let totalCount = 0;
      this.attendeeCounters.forEach(({ counter }) => (totalCount += counter));
      return totalCount;
    },
  },
  methods: {
    handleIncrease(index) {
      this.attendeeCounters[index].counter += 1;
    },
    handleDecrease(index) {
      this.attendeeCounters[index].counter -= 1;
    },
  },
};
</script>

<style></style>
