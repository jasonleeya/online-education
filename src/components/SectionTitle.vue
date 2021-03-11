<template>
<div class="title_comp">
  <slot></slot>
</div>
</template>

<script>
export default {
  name: "SectionTitle"
}
</script>

<style scoped>
.title_comp {
  font-size: 24px;
  color: #333;
  margin: 28px 0;
}
</style>