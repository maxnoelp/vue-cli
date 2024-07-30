<template>
  <button :class="`btn--${this.variant}`" @click="$emit('btn-clicked')">{{ text }}</button>
</template>

<script>
export default {
  emits: ['btn-clicked'],
  props: {
    text: {
      type: String,
      required: true,
    },
    variant: {
      type: String,
      default: 'primary',
      validator(propValue) {
        return ['primary', 'secondary'].includes(propValue);
      },
    },
  },
  // computed: {
  //   styling() {
  //     return ['btn', `btn--${this.variant}`];
  //   },
  // },
};
</script>

<style scoped>
:root {
  --primary: #6a1cc3;
  --primary-dark: #370b68;
  --secondary: #f39c12;
}

.btn {
  border: 3px solid transparent;
  border-radius: 3px;
  padding: 5px;
  cursor: pointer;
}

.btn--primary {
  border-color: Black;
  background-color: var(--primary);
  color: #fff;
}

.btn--primary:hover {
  border-color: var(--primary);
  background-color: var(--primary-dark);
}

.btn--secondary {
  border-color: var(--primary);
  background-color: transparent;
  color: var(--primary);
}

.btn--secondary:hover {
  background-color: var(--primary);
  color: #fff;
}
</style>
