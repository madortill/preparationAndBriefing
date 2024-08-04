<template>
    <div class="confetti-wrapper">
      <canvas ref="canvas" class="confetti-canvas"></canvas>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Confetti',
    data() {
      return {
        confettiArray: [],
        numConfetti: 100,
        colors: ['#ff87ab', '#fb6f92', '#fbf8cc', '#ffee99', '#ff4d6d', '#c9184a'],
      };
    },
    mounted() {
      this.setupCanvas();
      this.generateConfetti();
      this.animateConfetti();
    },
    methods: {
      setupCanvas() {
        const canvas = this.$refs.canvas;
        this.ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        window.addEventListener('resize', this.setupCanvas);
      },
      generateConfetti() {
        for (let i = 0; i < this.numConfetti; i++) {
          this.confettiArray.push(this.createConfetti());
        }
      },
      createConfetti() {
        return {
          x: Math.random() * window.innerWidth,
          y: Math.random() * window.innerHeight,
          size: Math.random() * 10 + 5,  // Size of the square confetti
          color: this.colors[Math.floor(Math.random() * this.colors.length)],
          velocityX: Math.random() * 2 - 1,  // Horizontal speed
          velocityY: Math.random() * 5 + 2,  // Vertical speed
        };
      },
      animateConfetti() {
        this.ctx.clearRect(0, 0, window.innerWidth, window.innerHeight);
  
        for (const confetti of this.confettiArray) {
          this.ctx.beginPath();
          this.ctx.rect(confetti.x, confetti.y, confetti.size, confetti.size);
          this.ctx.fillStyle = confetti.color;
          this.ctx.fill();
  
          confetti.x += confetti.velocityX;
          confetti.y += confetti.velocityY;
  
          if (confetti.y > window.innerHeight) {
            confetti.y = -confetti.size; // Reset to the top of the screen
            confetti.x = Math.random() * window.innerWidth; // Random horizontal position
          }
  
          if (confetti.x > window.innerWidth || confetti.x < -confetti.size) {
            confetti.x = Math.random() * window.innerWidth; // Reset horizontal position
            confetti.y = -confetti.size; // Reset to the top of the screen
          }
        }
  
        requestAnimationFrame(this.animateConfetti);
      }
    },
    beforeDestroy() {
      window.removeEventListener('resize', this.setupCanvas);
    }
  };
  </script>
  
  <style scoped>
  .confetti-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    pointer-events: none;
    z-index: 9999;
  }
  
  .confetti-canvas {
    position: absolute;
    top: 0;
    left: 0;
  }
  </style>
  