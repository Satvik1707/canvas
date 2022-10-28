<template><div></div> </template>

<style lang="css" scoped>
* {
  margin: 0;
  padding: 0;
}

.view {
  padding: 0 13% 0% 13%;
}

.att-container {
  display: flex;
  width: 100%;
  height: 50px;
  justify-content: space-between;
}

.att-first-up-line,
.att-second-up-line {
  flex: 1;
}

.att-first-up-line {
  height: 50px;
  width: 1px;
  border: 1px dashed black;
  border-left: 0;
  border-top: 0;
  max-width: calc(13%);
}

.att-second-up-line {
  height: 50px;
  max-width: calc(13%);
  border: 1px dashed black;
  border-right: 0;
  border-top: 0;
}

.att-first-down-line,
.att-second-down-line {
  flex: 1;
}

.att-first-down-line {
  height: 50px;
  border: 1px dashed black;
  border-left: 0;
  border-bottom: 0;
  margin-top: -1px;
  max-width: calc(13%);
}

.att-second-down-line {
  height: 50px;
  max-width: calc(13%);
  margin-top: -1px;
  border: 1px dashed black;
  border-right: 0;
  border-bottom: 0;
}

.container {
  display: flex;
  flex-direction: column;
  border: 1px dashed black;
  padding: 5%;
}

.container .header {
  font-size: 2em;
  font-family: Poppins, sans-serif;
  font-weight: 600;
  border-bottom: 1px solid #1c1c1d;
}

.container .description {
  margin-top: 30px;
  font-family: Poppins, sans-serif;
}

.container .read-more {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 0;
  background-color: transparent;
  color: #928c00;
  width: 140px;
  height: 60px;
  align-self: flex-end;
  margin-top: 20px;
  margin-right: 10px;
  font-size: 1em;
  font-family: Poppins, sans-serif;
  border: 1px solid black;
  cursor: pointer;
  transition: transform 0.3s;
}

.container .read-more:hover {
  transform: rotate(-10deg);
}

.container .read-more img {
  width: 20px;
  height: 20px;
  margin-left: 8px;
}

.read-more a {
  text-decoration: none;
  outline: none;
  color: #928c00;
}

/* 
.about .header {
    font-size: 3em;
    font-family: Poppins,sans-serif;
    margin:0;
} */
</style>

<script>
export default {}
</script>
