<template>
  <div></div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
}

.header {
  display: flex;
  width: 100%;
  justify-content: center;
  align-items: center;
  margin-top: 3em;
}

.header p {
  font-size: 2em;
  padding-left: 3%;
  padding-right: 3%;
  text-align: center;
  white-space: nowrap;
}

.header .line {
  width: 100%;
  height: 1px;
  right: 0;
  background-color: #928c00;
}

.container {
  display: flex;
  flex-wrap: wrap;
  padding: 5%;
  padding-left: 10%;
}

.container .info {
  display: flex;
  flex-direction: column;
  flex-grow: 2;
  max-width: 70%;
}

.container .contact {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  min-width: 30%;
}
.info-text {
  padding-bottom: 3vw;
  font-size: 1.5em;
  font-family: Poppins, sans-serif;
  max-width: 90%;
}

.info-information {
  display: flex;
  flex-wrap: wrap;
  min-width: 20%;
}

.info-address {
  flex-grow: 1;
}

.info-address p:first-child {
  font-size: 0.8em;
  color: gray;
}

.info-address p:last-child {
  line-height: 2;
}

.info-social {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.email {
  flex: 1;
}

.email p:first-child {
  font-size: 0.8em;
  color: gray;
}

.call-us {
  margin-top: 10px;
  flex: 1;
}

.call-us p:first-child {
  font-size: 0.8em;
  color: gray;
}

.contact {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: -4%;
}

.contact ul {
  list-style: none;
  margin-top: 15px;
  margin-bottom: 10px;
}

.contact .att-1 {
  width: 1px;
  height: 35%;
  background-color: #928c00;
}

@media (max-width: 575.98px) {
  .container {
    padding-bottom: 13%;
  }
}
</style>

<script>
export default {}
</script>
