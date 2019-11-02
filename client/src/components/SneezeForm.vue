<template>
  <div>
    <form @submit="recordSneeze">
      <input type="date" v-model="sneezeDate" />
      <input type="time" v-model="sneezeTime" />
      <input type="submit" value="Add" />
    </form>
  </div>
</template>

<script>
export default {
  name: "SneezeForm",
  data() {
    return {sneezeDate: "", sneezeTime: ""}
  },
  methods: {
    recordSneeze(e) {
      e.preventDefault();

      const newSneeze = {
        date: this.sneezeDate,
        time: this.sneezeTime
      }

      // send up to parent
      this.$emit('record-sneeze', newSneeze);

      // reset form placeholder?
      this.sneezeDate = "";
      this.sneezeTime = "";
    }
  }
}
</script>

<style scoped>

</style>