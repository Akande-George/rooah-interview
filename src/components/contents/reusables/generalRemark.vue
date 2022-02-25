<template>
  <div class="q-pa-md">
    <label for="">General remark</label>
    <q-input v-model="remark" dense outlined type="textarea" />
    <div class="q-pt-md" align="right">
      <q-btn color="red" label="cancel" />
      <q-btn
        color="blue-grey-10"
        class="q-ml-md"
        label="save expenditure transactions"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      remark: "",
    };
  },
};
</script>

<style>
</style>