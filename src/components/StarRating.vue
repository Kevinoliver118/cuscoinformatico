<template>
  <div class="star-rating">
    <span
      v-for="star in stars"
      :key="star"
      @click="setRating(star)"
      @mouseover="hoverRating = star"
      @mouseleave="hoverRating = rating"
      class="star"
      :class="{ filled: star <= (hoverRating || rating) }"
    >
      ★
    </span>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      stars: [1, 2, 3, 4, 5],
      hoverRating: 0
    };
  },
  computed: {
    rating() {
      return this.value;
    }
  },
  methods: {
    setRating(star) {
      this.$emit('input', star);
    }
  }
};
</script>

<style scoped>
.star {
  cursor: pointer;
  font-size: 24px;
  color: #ccc;
}

.star.filled {
  color: #ffcc00;
}
</style>
