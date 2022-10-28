<template>
  <div class="container">
    <div class="left-column">
      <p class="att-1">20' x 21'</p>
      <div class="att-2">
        <div class="att-arrow att-arrow-up-triangle" />
        <div class="att-arrow-up-line" />
        <p class="att-text">24</p>
        <div class="att-arrow-down-line" />
        <div class="att-arrow att-arrow-down-triangle" />
      </div>
      <canvas id="canvas" ref="drawCanvas"></canvas>
      <canvas
        id="canvas"
        ref="canvas"
        @mousedown="startPainting"
        @mouseup="finishedPainting"
        @mousemove="draw"
      ></canvas>
      <div class="left-column-text">
        <p class="main-text">Scribble here</p>
        <p class="main-text-desc" align="center">Avyukt World</p>
        <button class="contact-us" @click="redirect()">Go to website</button>
      </div>

      <div class="paint-nav">
        <div class="tools">
          <img
            class="tool-icon"
            :class="{ active: drawingType == 0 }"
            src="../assets/brush.svg"
            v-on:click="changeDrawing(0)"
          />
          <img
            class="tool-icon"
            :class="{ active: drawingType == 1 }"
            src="../assets/diagonal-line.svg"
            v-on:click="changeDrawing(1)"
          />
          <img
            class="tool-icon"
            :class="{ active: drawingType == 2 }"
            src="../assets/square.svg"
            v-on:click="changeDrawing(2)"
          />
          <img
            class="tool-icon"
            src="../assets/erase.svg"
            v-on:click="clearDrawCanvas()"
          />
        </div>
      </div>
      <!-- <div class="att-3">
        <div class="att-step-line"></div>
        <div class="att-step-line"></div>
        <div class="att-step-line"></div>
        <div class="att-step-line"></div>
        </div> -->
    </div>
  </div>
</template>

<style lang="css" scoped>
* {
  padding: 0;
  margin: 0;
}
.contact-us {
  width: 140px;
  height: 50px;
  border: none;
  outline: none;
  color: #fff;
  font-family: Poppins, sans-serif;
  font-weight: 700;
  background: #111;
  cursor: pointer;
  position: relative;
  z-index: 0;
  border-radius: 25px;
  margin-left: 20px;
  left: 23%;
}

.contact-us:before {
  content: '';
  background: linear-gradient(
    45deg,
    #ff0000,
    #ff7300,
    #fffb00,
    #48ff00,
    #00ffd5,
    #002bff,
    #7a00ff,
    #ff00c8,
    #ff0000
  );
  position: absolute;
  top: -2px;
  left: -2px;
  background-size: 400%;
  z-index: -1;
  filter: blur(5px);
  width: calc(100% + 4px);
  height: calc(100% + 4px);
  animation: glowing 20s linear infinite;
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
  border-radius: 25px;
}

.contact-us:active {
  color: #000;
}

.contact-us:active:after {
  background: transparent;
}

.contact-us:hover:before {
  opacity: 1;
}

.contact-us:after {
  z-index: -1;
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: #111;
  left: 0;
  top: 0;
  border-radius: 25px;
}

@keyframes glowing {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}
.container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  height: 88vh;
  width: auto;
}

.left-column {
  display: flex;
  position: relative;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-grow: 2;
  padding: 10em 3em 10em 3em;
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

.left-column-text {
  margin-left: 40px;
}

.left-column .main-text-desc {
  color: #928c00;
  font-size: 1.9em;
  font-family: Poppins, sans-serif;
  flex-direction: row;
}

.left-column .main-text {
  color: #1c1c1d;
  font-size: 3em;
  font-weight: 900;
  font-family: Poppins, sans-serif;
  line-height: 60px;
  margin: 10px 0 10px 0;
}

.left-column .main-text-intro {
  font-family: Poppins, sans-serif;
  font-size: 2em;
}

#canvas {
  display: block;
  width: 100%;
  height: 100%;
  top: 0;
  position: absolute;
}

.paint-nav {
  display: flex;
  position: absolute;
  bottom: 0;
  margin: auto;
  height: 50px;
  background-color: #eeece5;
  border: 1px solid black;
  border-bottom: 0;
  border-top-left-radius: 25px;
  border-top-right-radius: 25px;
}

.tools {
  display: flex;
  align-items: center;
  flex: 1;
  padding: 10px;
  padding-top: 20px;
  padding-bottom: 20px;
}

.tool-icon {
  width: 24px;
  height: 24px;
  margin-right: 14px;
  transition: padding 0.3s ease;
  cursor: pointer;
}

.tool-icon:last-of-type {
  margin-right: 0;
}

/* .colors {
  display: flex;
  align-items: center;
  flex:1;
  border-left: 1px solid grey;
  padding-left: 12px;
}

.color {
  width: 24px;
  height: 24px;
  border-radius: 30px;
  margin-right: 10px;
} */

.right-column {
  display: flex;
  justify-content: center;
  align-items: center;
  border-left: 1px solid black;
  border-right: 1px solid black;
  flex-grow: 2;
  max-width: 500px;
  margin-right: 3em;
  -webkit-box-shadow: -14px 3px 52px -26px #0000007a;
  -moz-box-shadow: -14px 3px 52px -26px #0000007a;
  box-shadow: -14px 3px 52px -26px #0000007a;
  /* background:url(
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAICAYAAADED76LAAAAMklEQVQoU2NkwA/+M+KR/8/AwMCISwFYEqQZmwK4JDYFKJLoCjAkkRVglYQpwCkJUgAAGOQICDcTvB4AAAAASUVORK5CYII=
   ) repeat; */
}

.right-column img {
  border-top: 1px solid black;
  border-bottom: 1px solid black;
  max-width: 70%;
  max-height: 70%;
  padding: 15%;
  /* filter: grayscale(100%) ; */
}

.att-1 {
  display: block;
  position: absolute;
  right: 0px;
  top: 0px;
  padding: 10px 10px 10px 10px;
  text-align: center;
  font-family: Poppins, sans-serif;
  border-left: 1px solid black;
  border-bottom: 1px solid black;
}

.att-2 {
  position: absolute;
  left: 2em;
  margin-right: 2em;
}

.att-2 .att-arrow-up-line {
  width: 0.1em;
  height: 7em;
  margin-bottom: 0.9em;
  margin-left: 0.95em;
  background-color: #1c1c1d;
}

.att-2 .att-arrow-up-triangle {
  transform: rotate(-135deg);
  -webkit-transform: rotate(-135deg);
  margin-bottom: -0.55em;
}

.att-arrow {
  border: solid black;
  border-width: 0 2.5px 2.5px 0;
  padding: 3px;
  display: inline-block;
  margin-left: 11.5px;
}

.att-2 .att-arrow-down-triangle {
  transform: rotate(45deg);
  -webkit-transform: rotate(45deg);
  position: absolute;
  margin-top: -4px;
}

.att-2 .att-arrow-down-line {
  width: 0.1em;
  height: 7em;
  margin-top: 15px;
  margin-left: 15px;
  background-color: #1c1c1d;
}

.att-2 .att-text {
  transform: rotate(-90deg);
  font-size: 1em;
  margin-left: 0.3em;
  font-family: Poppins, sans-serif;
}

.active {
  padding-bottom: 8px;
  border-bottom: 2px solid #928c00;
}

/* 
.att-3 {
  position: absolute;
  bottom: 0;
  width: 100px;
  height: 100px;
  margin-left: 30%;
  border: 1px solid black;
  border-bottom: none;
  padding-top: 3px;
}


.att-3 .att-step-line {
  width: 100%;
  height: 1px;
  background-color: black;
  margin-top: 19px;
} */

@media (max-width: 575.98px) {
  .left-column {
    padding: 10% 10% 35% 10%;
    border-bottom: 1px solid black;
  }

  .left-column .main-text-desc {
    color: #928c00;
    font-size: 1.3em;
    font-family: Poppins, sans-serif;
  }

  .left-column .main-text {
    color: #1c1c1d;
    font-size: 3em;
    font-weight: 900;
    font-family: Poppins, sans-serif;
    line-height: 60px;
    margin: 10px 0 30px 0;
  }

  .left-column .main-text-intro {
    font-family: Poppins, sans-serif;
    font-size: 1.5em;
  }
}

/* Small devices (landscape phones, less than 768px) */
@media (max-width: 767.98px) {
}

/* // Medium devices (tablets, less than 992px) */
@media (max-width: 991.98px) {
}

/* // Large devices (desktops, less than 1200px) */
@media (max-width: 1265.98px) {
  .right-column {
    display: none;
  }
}
</style>

<script>
export default {
  data() {
    return {
      painting: false,
      ctx: null,
      drawCtx: null,
      drawingType: 0,
      startPoint: {},
      endPoint: {}
    }
  },
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
    this.drawCtx = this.$refs.drawCanvas.getContext('2d')
    this.setSizesOfCanvas()
  },
  methods: {
    startPainting(e) {
      this.painting = true
      if (this.drawingType != 0) {
        if (
          this.$refs.canvas.clientHeight != this.$refs.canvas.height ||
          this.$refs.canvas.width != this.$refs.canvas.clientWidth
        ) {
          this.setSizesOfCanvas()
        }
        this.startPoint = this.getMousePos(this.$refs.drawCanvas, e)
        return
      }
      this.draw(e)
    },
    finishedPainting(e) {
      this.painting = false

      this.drawCtx.lineWidth = 2
      this.drawCtx.lineCap = 'square'
      this.drawCtx.strokeStyle = '#535353'
      if (this.drawingType == 0) {
        this.drawCtx.lineWidth = 7
        this.drawCtx.lineCap = 'round'
        this.drawCtx.beginPath()
      } else if (this.drawingType == 1) {
        this.endPoint = this.getMousePos(this.$refs.drawCanvas, e)
        this.drawCtx.beginPath()
        this.drawCtx.moveTo(this.startPoint.x, this.startPoint.y)
        this.drawCtx.lineTo(this.endPoint.x, this.endPoint.y)
        this.drawCtx.stroke()
        this.clearCanvas()
      } else if (this.drawingType == 2) {
        this.endPoint = this.getMousePos(this.$refs.drawCanvas, e)
        var rect = {
          width: this.endPoint.x - this.startPoint.x,
          height: this.endPoint.y - this.startPoint.y
        }
        this.drawCtx.strokeRect(
          this.startPoint.x,
          this.startPoint.y,
          rect.width,
          rect.height
        )
        this.clearCanvas()
      }
    },
    draw(e) {
      if (!this.painting) return

      this.endPoint = this.getMousePos(this.$refs.canvas, e)

      this.ctx.lineWidth = 2
      this.ctx.lineCap = 'square'
      this.ctx.strokeStyle = '#535353'

      if (this.drawingType == 0) {
        this.drawCtx.lineWidth = 7
        this.drawCtx.lineCap = 'round'
        this.drawCtx.strokeStyle = '#535353'
        this.drawCtx.lineTo(this.endPoint.x, this.endPoint.y)
        this.drawCtx.stroke()
        this.drawCtx.beginPath()
        this.drawCtx.moveTo(this.endPoint.x, this.endPoint.y)
      } else if (this.drawingType == 1) {
        this.clearCanvas()
        this.ctx.beginPath()
        this.ctx.moveTo(this.startPoint.x, this.startPoint.y)
        this.ctx.lineTo(this.endPoint.x, this.endPoint.y)
        this.ctx.stroke()
      } else if (this.drawingType == 2) {
        this.clearCanvas()
        var rect = {
          width: this.endPoint.x - this.startPoint.x,
          height: this.endPoint.y - this.startPoint.y
        }
        this.ctx.strokeRect(
          this.startPoint.x,
          this.startPoint.y,
          rect.width,
          rect.height
        )
      }
    },
    getMousePos(canvas, evt) {
      var rect = canvas.getBoundingClientRect()
      return {
        x:
          ((evt.clientX - rect.left) / (rect.right - rect.left)) * canvas.width,
        y: ((evt.clientY - rect.top) / (rect.bottom - rect.top)) * canvas.height
      }
    },
    setSizesOfCanvas() {
      this.$refs.canvas.height = this.$refs.canvas.clientHeight
      this.$refs.canvas.width = this.$refs.canvas.clientWidth

      this.$refs.drawCanvas.height = this.$refs.drawCanvas.clientHeight
      this.$refs.drawCanvas.width = this.$refs.drawCanvas.clientWidth
    },
    clearCanvas() {
      this.ctx.clearRect(
        0,
        0,
        this.$refs.canvas.clientWidth,
        this.$refs.canvas.clientHeight
      )
    },
    clearDrawCanvas() {
      this.drawCtx.clearRect(
        0,
        0,
        this.$refs.drawCanvas.clientWidth,
        this.$refs.drawCanvas.clientHeight
      )
    },
    changeDrawing(index) {
      this.drawingType = index
      this.startPoint = {}
      this.endPoint = {}
      this.drawCtx.beginPath()
    },
    redirect() {
      window.open('https://avyukt.netlify.app')
    }
  }
}
</script>
