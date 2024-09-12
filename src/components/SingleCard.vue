<script>
export default {
  props: {
    card: Object
  }
}
</script>

<template>
  <div>
    <img :src="card.card_images[0].image_url" alt="" class="w-100">
    
    <div class="text p-3">
      <h5 class="text-white pb-2">
        {{ card.name }}
      </h5>

      <p>
        {{ card.archetype }}
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>

</style>
