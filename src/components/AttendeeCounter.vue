<template>
  <p>{{ text }} {{ counter }}</p>
  <button @click="increase">+</button>
  <button @click="decrease">-</button>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    text: String,
    counter: Number,
  },
  emits: ["increase", "decrease"],
  methods: {
    increase() {
      this.$emit("increase");
    },
    decrease() {
      this.$emit("decrease");
    },
  },
};
</script>
