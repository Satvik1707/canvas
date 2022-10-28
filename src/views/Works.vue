<template>
  <portfolio :id="this.id"></portfolio>
</template>

<style scoped></style>

<script>
import Portfolio from '../components/Portfolio.vue'
export default {
  props: {
    id: {
      type: String,
      required: true
    }
  },
  components: {
    Portfolio
  }
}
</script>
