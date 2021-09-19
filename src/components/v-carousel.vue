<template>
  <div class="wrapper"

  >
    <div class="v-carousel"
      :style="{'margin-left': '-' + (100 * currentSlideIndex) + '%'}"
    >
      <vCarouselItem
          v-for="item in carousel_data"
          :key="item.id"
          :item_data="item"
      >
      </vCarouselItem>
    </div>
    <div class="button-wrap">
      <button @click="prevSlide">Предыдущая</button>
      <button @click="nextSlide">Следующая</button>
    </div>
  </div>
</template>

<script>
import vCarouselItem from './v-carousel-item.vue'

export default {
  name: "v-carousel",
  components: {vCarouselItem},
  props: {
    carousel_data: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      currentSlideIndex: 0
    }
  },
  methods: {
    prevSlide() {
      if (this.currentSlideIndex !== 0) {
        this.currentSlideIndex--;
      } else{
        this.currentSlideIndex = this.carousel_data.length - 1;
      }
    },
    nextSlide() {
      if (this.currentSlideIndex < this.carousel_data.length - 1) {
        this.currentSlideIndex++;
      } else {
        this.currentSlideIndex = 0;
      }
    },
    autoChangeSlide(){
      this.nextSlide();
    },

  },

  mounted() {
    // let intervalId = setInterval(this.autoChangeSlide, 2000);
  }
}
</script>

<style scoped>
.wrapper {
  max-width: 300px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  color: #4b4156;
}

.v-carousel {
  display: flex;
  transition: all ease .5s;
}

.button-wrap {
  display: flex;
  justify-content: center;
}

.button-wrap button {
  margin: 10px;
}
</style>