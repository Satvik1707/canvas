<template>
  <iam-gunay></iam-gunay>
</template>

<style lang="css" scoped>
.space {
  height: 2vw;
  min-height: 30px;
  border-bottom: 1px solid black;
  border-top: 1px solid black;
  background-image: linear-gradient(
      #b8b8b8 1.2000000000000002px,
      transparent 1.2000000000000002px
    ),
    linear-gradient(
      to right,
      #b8b8b8 1.2000000000000002px,
      transparent 1.2000000000000002px
    );
  background-size: 24px 24px;
}

.first {
  border-top: 0;
  height: 0px;
  min-height: 0;
}
</style>

<script>
import IamGunay from '../components/IamGunay.vue'

export default {
  components: {
    IamGunay
  }
}
</script>
