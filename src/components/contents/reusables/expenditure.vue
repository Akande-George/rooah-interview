<template>
  <div class="">
    <div>
      <q-select
        outlined
        dense
        v-model="amountSel"
        class="q-py-sm"
        :options="options"
        placeholder="filed"
      >
        <template v-slot:prepend>
          <div class="select-acct text-caption text-weight-medium">
            Select Account
          </div>
        </template>
      </q-select>
      <q-select
        outlined
        dense
        v-model="weeks"
        class="q-py-sm"
        :options="week"
        placeholder="filed"
      >
        <template v-slot:prepend>
          <div class="select-acct text-caption text-weight-medium">
            Select Week
          </div>
        </template>
      </q-select>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      amountSel: "",
      weeks: "",
      options: ["1", "2"],
      week: ["week 0", "week 1", "week 2", "week 3"],
    };
  },
};
</script>

<style scoped>
/* .select-acct {
  border-top: 1px solid blue;
  border-bottom: 1px solid blue;
  border-left: 1px solid blue;
} */
</style>