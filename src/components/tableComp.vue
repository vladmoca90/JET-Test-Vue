<template>
  <div class="table__box">
    <h2 class="table__heading">JET Test</h2>
    <table class="table__content table table-dark table-hover">
      <tableHeading></tableHeading>
      <tbody>
        <tableRow v-for="preference in dataMain.Preferences" :key="preference.PreferenceCode" :preference="preference"></tableRow>
      </tbody>
    </table>
  </div>
</template>

<script>
import tableHeading from './tableHeading.vue'
import tableRow from './tableRow.vue'

export default {
  props: ['dataMain'],
  name: 'tableComp',
  components: {
    tableHeading,
    tableRow,
  },
};
</script>
<style lang="css" scoped>
.table__box {
  font-family: Tahoma;
  margin: 25px auto;
  max-width: 1100px;
  text-align: center;
  width: 100%;
}
.table__heading {
  margin-bottom: 40px;
}
</style>
