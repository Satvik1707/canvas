<template>
  <div></div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
}

.container {
  display: flex;
  flex-direction: column;
  padding-bottom: 4em;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 2em 0 2em;
}

.header p:first-child {
  margin-top: 2.5em;
  margin-bottom: 0.5em;
  font-size: 2em;
}
.header p:last-child {
  font-size: 1em;
  font-weight: 300;
}

.projects {
  display: flex;
  flex-wrap: wrap;
  margin-top: 6em;
}

.card {
  flex-grow: 1;
  display: block;
  width: calc(100% / 3 - 2px);
  width: 400px;
  height: 27vw;
  min-height: 350px;
  background-repeat: no-repeat;
  background-size: 100% 100%;
}

/* This code gives big size which is first item in works container */
.card:first-child {
  flex-grow: 3;
  width: calc(100% - (100% / 3) - 8px);
}

.card:first-child .left-column {
  max-width: 80%;
}

.card:hover .left-column {
  max-height: 85%;
}

.card-info .card-description {
  display: none;
}

.card:hover .card-info .card-description {
  display: inline;
}

.card:hover .bg-change {
  background-color: rgba(0, 0, 0, 0.65);
  backdrop-filter: blur(5px);
}

.bg-change {
  display: flex;
  width: 100%;
  height: 100%;
  transition: 0.3s background-color;
}

.left-column {
  display: flex;
  flex-direction: column;
  justify-self: flex-start;
  align-self: flex-end;
  margin-bottom: 35px;
  margin-left: 35px;
  max-width: 60%;
  flex-grow: 1;
  transition: 20s all;
}

/* P - is area and floors-count classes */
.left-column .card-info,
.right-column p {
  flex: 1;
  font-size: 1.3em;
  color: white;
}

.left-column .card-description {
  font-size: 0.7em;
}

.left-column .card-info {
  margin-bottom: 15px;
}

.left-column .read-more {
  cursor: pointer;
  width: 100px;
  background: transparent;
  border: 0;
  border-bottom: 1px solid #928c00;
  color: white;
  order: 2s;
}

.left-column .read-more img {
  width: 20px;
  height: 20px;
  margin-left: 5px;
  transform: rotate(180deg);
}

.read-more a {
  display: flex;
  justify-items: center;
  align-items: center;
  flex-direction: row;
  text-decoration: none;
  color: white;
  outline: none;
}

.right-column {
  display: flex;
  flex-direction: column;
  justify-self: flex-end;
  align-self: flex-end;
  justify-items: flex-end;
  align-items: flex-end;
  margin-bottom: 35px;
  margin-right: 35px;
  flex-grow: 1;
}

.right-column .floor-count {
  margin-bottom: 15px;
  font-size: 0.9em;
}

.right-column .area {
  display: flex;
  flex-direction: row;
  justify-items: center;
  align-items: center;
  font-size: 1em;
}

.right-column .area img {
  margin-right: 10px;
}
</style>

<script>
import backgroundUrl1 from '../assets/item-1.jpg'
import backgroundUrl2 from '../assets/item-2.jpg'
import backgroundUrl3 from '../assets/item-3.jpg'
import backgroundUrl4 from '../assets/item-4.jpg'
import backgroundUrl5 from '../assets/item-5.jpg'
export default {
  data() {
    return {
      items: [
        {
          message: 'Foo',
          image: backgroundUrl1
        },
        {
          message: 'Bar',
          image: backgroundUrl2
        },
        {
          message: 'Bar',
          image: backgroundUrl3
        },
        {
          message: 'Bar',
          image: backgroundUrl4
        },
        {
          message: 'Bar',
          image: backgroundUrl5
        }
      ]
    }
  }
}
</script>
