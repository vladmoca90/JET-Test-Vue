<template>
<tr>
  <td>{{ preference.ControllerCode }}</td>
  <td>{{ preference.PreferenceCode }}</td>
  <td>{{ preference.Name }}</td>
  <td>{{ preference.Description }}</td>
  <td>{{ preference.Status }}</td>
</tr>
</template>

<script>
export default {
  props: ['preference'],
}
</script>
<style lang="css" scoped>
.table__content > thead > th,
.table__content > tbody > tr > td {
  padding: 10px 15px;
}
.table__content > tbody > tr > td {
  cursor: pointer;
  font-size: 12px;
  vertical-align: middle;
}
</style>
