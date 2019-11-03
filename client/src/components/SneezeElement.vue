<template>
  <!-- ensure not empty and valid date and time before posting - either pre HTTP post or here -->
  <p>{{sneeze.date}}   {{sneeze.time}}</p>
</template>

<script>
export default {
  name: "SneezeElement",
  props: ["sneeze"]
}
</script>

<style scoped>

</style>