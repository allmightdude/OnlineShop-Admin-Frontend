<template>
  <button class="btn" :class="[mode , border , size]">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    mode: {
      type: String,
      required: false,
      default : 'orange'
    },
    border: {
      type: String,
      required: false,
    },
    size: {
      type: String,
      required: false,
      default : 'lg-size'
    },
    
  },
};
</script>

<style lang="scss" scoped>
.btn {
  border-radius: 5px;
  color: #2c3e50;
  border: none;
  background-color: transparent;
}

.orange {
  background-color: #f1c40f;
  border: 1px solid #c2c2c2;
}

.btn__grey {
  background-color: #f2f2f2;
}

.sm-size {
  padding: 0.5rem;
}

.border{
    border: 1px solid #C2C2C2;
}
.lg-size {
  padding: .5rem 2rem;
}
</style>
