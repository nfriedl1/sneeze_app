<template>
  <!-- <div>
    <SneezeElement v-bind:key="sneeze.id" v-for="sneeze in sneezes" />
  </div> -->
  <div>
    <div v-bind:key="sneeze.id" v-for="sneeze in sneezes">
      <SneezeElement v-bind:sneeze="sneeze" />
    </div>
  </div>
</template>

<script>
import SneezeElement from './SneezeElement.vue';

export default {
  name: "SneezeList",
  components: {SneezeElement},
  props: ["sneezes"]
}
</script>

<style scoped>

</style>