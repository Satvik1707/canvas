<template>
  <footer></footer>
</template>
<style scoped>
footer {
  display: flex;
  align-items: center;
  height: 70px;
  padding-left: 10%;
  padding-right: 10%;
  padding-top: 20px;
  padding-bottom: 10px;
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

p {
  color: #1c1c1d;
}

@media (max-width: 575.98px) {
  footer {
    padding-top: 30px;
    padding-bottom: 20px;
  }
}
</style>
