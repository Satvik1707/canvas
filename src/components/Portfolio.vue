<template>
  <div class="container">
    <div class="project-info">
      <div class="project-title">
        {{ current_project.name }}
      </div>

      <p class="sidebar">Location</p>
      <p>{{ current_project.location }}</p>
      <p class="sidebar">Owner</p>
      <p>{{ current_project.owner }}</p>
      <p class="sidebar">Date</p>
      <p>{{ current_project.date }}</p>

      <div class="project-description">
        {{ current_project.description }}
      </div>

      <div class="project-nav">
        <div class="prev">
          <button v-on:click="previous()" class="previous-button">
            <img
              class=""
              src="../assets/arrow-right.svg"
              width="32"
              height="32"
              alt="previos project"
            />
            <p>Previous</p>
          </button>
        </div>
        <div class="next">
          <button v-on:click="next()" class="next-button">
            <p>Next</p>
            <img
              src="../assets/arrow-right.svg"
              width="32"
              height="32"
              alt="previos project"
            />
          </button>
        </div>
      </div>
    </div>
    <div class="project-content">
      <div class="project-header">
        {{ current_project.description }}
      </div>
      <img
        class="project-item"
        v-for="item in current_project.images"
        :key="item"
        :src="item"
        v-on:click="openImage(item, name)"
      />
    </div>
  </div>
  <div id="myModal" class="modal" ref="modal">
    <!-- The Close Button -->
    <span class="close" v-on:click="closeImage()">&times;</span>

    <!-- Modal Content (The Image) -->
    <div class="modal-content">
      <img class="modal-content" id="img" ref="img" />
      <!-- Modal Caption (Image Text) -->
      <div id="caption" ref="caption"></div>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  font-family: Poppins, sans-serif;
  box-sizing: border-box;
}

.container {
  display: flex;
  position: relative;
}

.project-info {
  display: flex;
  flex: 2;
  flex-direction: column;
  position: sticky;
  max-height: 100vh;
  min-height: 100vh;
  width: 100%;
  top: 0;
  padding-left: 30px;
  padding-top: 30px;
  padding-right: 30px;
  border: 1px solid black;
  border-top: 0;
}

.project-title {
  font-weight: 900;
  font-size: 2em;
  text-transform: uppercase;
}

.sidebar:first-of-type {
  margin-top: 40px;
}

.sidebar {
  font-weight: 600;
}

.project-description {
  margin-top: 40px;
  margin-bottom: 80px;
  line-height: 18px;
}

.project-content {
  display: flex;
  flex-direction: column;
  position: relative;
  justify-content: flex-start;
  width: 100%;
  margin-top: 100px;
  padding-left: 40px;
  padding-right: 40px;
  padding-bottom: 40px;
  border-top: 1px solid black;
  border-bottom: 1px solid black;
  flex: 5;
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

.project-content img {
  max-width: 100%;
}

.project-header {
  font-weight: 900;
  font-size: 2.3vw;
  line-height: 95%;
  padding-top: 30px;
}

.project-item {
  margin-top: 5%;
}

.project-nav {
  display: flex;
  justify-self: flex-end;
  align-items: flex-end;
  flex-grow: 1;
  padding-bottom: 10%;
}

.prev {
  display: flex;
  flex: 1;
  justify-content: flex-start;
}

.next {
  display: flex;
  justify-content: flex-end;
  flex: 1;
}

.previous-button,
.next-button {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: transparent;
  border: 0;
  flex: 1;
  padding: 8px;
  cursor: pointer;
}

.previous-button img {
  margin-right: 7px;
  transform: rotate(180deg);
}

.next-button img {
  margin-left: 7px;
}

.modal {
  display: none; /* Hidden by default */
  flex-direction: column;
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  justify-content: center;
  align-items: center;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  /* Black w/ opacity */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.9);
  backdrop-filter: blur(8px);
}
.modal-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  max-width: 800px;
}
.modal-content img {
  max-width: 800px;
}
#caption {
  display: flex;
  justify-content: center;
  text-align: center;
  color: #ccc;
  padding: 10px 0;
  height: 20px;
  font-size: 1.2em;
  text-transform: capitalize;
  font-family: Poppins, sans-serif;
}
.modal-content,
#caption {
  animation-name: zoom;
  animation-duration: 0.5s;
}
@keyframes zoom {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(1);
  }
}
.close {
  position: absolute;
  top: 15px;
  right: 35px;
  color: #f1f1f1;
  font-size: 40px;
  font-weight: bold;
  transition: 0.3s;
}
.close:hover,
.close:focus {
  color: #bbb;
  text-decoration: none;
  cursor: pointer;
}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (max-width: 1025px) {
  .container {
    display: flex;
    flex-direction: column;
  }

  .project-info {
    position: static;
    width: auto;
    min-height: 0;
    max-height: none;
  }

  .project-description {
    margin-bottom: auto;
  }

  .project-content {
    display: flex;
    padding: 0px;
    margin-top: 0;
    border-top: 0;
  }

  .project-header {
    font-size: 22px;
    padding-left: 30px;
    padding-right: 30px;
    font-weight: 700;
  }

  .project-item {
    padding-left: 30px;
    padding-right: 30px;
  }

  .project-item:last-of-type {
    padding-bottom: 30px;
  }

  .project-nav {
    margin-top: 30px;
  }
}
</style>

<script>
import projectData from '../assets/data/projects.json'
export default {
  props: {
    id: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      current_project: {},
      current_id: 0
    }
  },
  created() {
    if (this.id) {
      this.current_id = this.id
    }
    this.current_project = projectData[this.current_id]
  },
  methods: {
    next() {
      if (this.current_id + 1 == Object.keys(projectData).length) {
        this.current_id = 0
      } else {
        this.current_id = this.current_id + 1
      }
      this.current_project = projectData[this.current_id]
    },
    previous() {
      if (this.current_id - 1 == -1) {
        this.current_id = Object.keys(projectData).length - 1
      } else {
        this.current_id = this.current_id - 1
      }
      this.current_project = projectData[this.current_id]
    },
    openImage(src, alt) {
      this.$refs.modal.style.display = 'flex'
      this.$refs.img.src = src
      this.$refs.caption.textContent = alt
    },
    closeImage() {
      this.$refs.modal.style.display = 'none'
    }
  }
}
</script>
