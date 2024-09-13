<template>
    
  <main>
    <section class="card" :style="{ backgroundColor: boxColor }">
      <h2>1. Click Counter & Box Color Changer</h2>
      <div class="content">
        <p class="count">Count: {{ count }}</p>
        <div class="btngroup">
          <button @click="incrementCount" class="btn" :style="{ backgroundColor: btnColor }">+</button>
          <button @click="decrementCount" class="btn" :style="{ backgroundColor: btnColor }">-</button>
          <button @click="multiplyCount" class="btn" :style="{ backgroundColor: btnColor }">x2</button>
        </div>
        <button @click="resetcount" class="btn" :style="{ backgroundColor: btnColor }">Reset</button>
        <button @click="changeColor" class="btn" :style="{ backgroundColor: btnColor }">Change Color</button>
      </div>
      <h2>2. Image Carousel</h2>
      <div class="content">
        <img :src="currentImage" alt="Carousel Image" class="carousel-image" />
        <div class="carousel-controls">
          <button @click="prevImage" class="btn" :style="{ backgroundColor: btnColor }">Previous</button>
          <button @click="nextImage" class="btn" :style="{ backgroundColor: btnColor }">Next</button>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
  export default {
    data() {
      return {
        count: 0,
        boxColor: 'lightblue',
        images: [
          'https://picsum.photos/id/1020/400/300',
          'https://picsum.photos/id/1010/400/300',
          'https://picsum.photos/id/1012/400/300',
          'https://picsum.photos/id/1026/400/300',
          'https://picsum.photos/id/1029/400/300'
        ],
        currentImageIndex: 0,
      };
    },
    
    computed: {
      currentImage() {
        return this.images[this.currentImageIndex];
      },
    },
    
    methods: {
      incrementCount() {
        this.count++;
      },

      decrementCount() {
        this.count--;
      },

      multiplyCount() {
        this.count *= 2;
      },

      resetcount() {
        this.count = 0;
      },
      
      changeColor() {
        this.boxColor = `rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255})`;
        this.btnColor = `rgb(${Math.random() * 155}, ${Math.random() * 155}, ${Math.random() * 155})`;
      },
      
      nextImage() {
        this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
      },
      
      prevImage() {
        this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length;
      },
    },
  };
</script>

<style scoped>

h1 {
  margin: 0;
}

main {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px 0;
}

.card {
  background-color: white;
  font-weight: heavy;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

h2 {
  color: var(--primary-color);
  margin-top: 0;
  margin-bottom: 30px;
  font-weight: bold;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn {
  background-color: rgb(109, 109, 109);
  color: rgb(255, 252, 252);
  font-weight: heavy;
  border: none;
  padding: 10px 20px;
  margin: 10px 0;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btngroup {
  display: flex;
  gap: 10px;
}

.count {
  font-size: 24px;
  font-weight: bold;
  color: var(--primary-color);
}

.color-box {
  width: 100px;
  height: 100px;
  margin: 10px 0;
  border-radius: 8px;
  transition: background-color 0.3s;
}

.carousel-image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  border: 5px solid black;
}

.carousel-controls {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin-top: 10px;
}
</style>