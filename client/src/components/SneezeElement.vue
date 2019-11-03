<template>
  <p>{{sneeze.date}} {{sneeze.time}}</p>
</template>

<script>
export default {
  name: "SneezeElement",
  props: ["sneeze"]
}
</script>

<style scoped>

</style>