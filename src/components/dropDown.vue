<template>

  <h1 style="margin-top: 50px;">
    {{ title }}
    <button @click="open = !open">
      {{ !!open ? "-" : "+" }}
    </button>
  </h1>
  <a :href="link">Source</a>

  <div v-if="open">
    <slot></slot>
  </div>

</template>

<script>
export default {
  name: "dropDown",
  props: {
    title: {
      type: String,
      required: true,
    },
    link: {
      type: String
    }
  },
  data () {
    return {
      open: false
    }
  }
}
</script>

<style scoped>

</style>