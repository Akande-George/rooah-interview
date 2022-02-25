<template>
  <div class="q-pa-lg bg-grey-2 text-grey">
    <q-card class="q-pa-lg">
      <q-card flat>
        <q-tabs
          v-model="tab"
          dense
          class="text-grey half-width"
          active-color="black"
          indicator-color="primary"
          align="left"
        >
          <q-tab name="revenue" label="Revenue Sheets" no-caps />
          <q-tab name="expenditure" label="Expenditure sheets" no-caps />
        </q-tabs>

        <!-- <q-separator /> -->

        <q-tab-panels v-model="tab" animated>
          <q-tab-panel name="revenue">
            <Expenditure />
            <div class="q-pt-md">
              <ExpenditureTable />
            </div>
          </q-tab-panel>

          <q-tab-panel name="expenditure">
            <Expenditure />
            <div class="q-pt-md">
              <ExpenditureTable />
            </div>
            <div class="q-pt-md">
              <GeneralRemark />
            </div>
          </q-tab-panel>
        </q-tab-panels>
      </q-card>
    </q-card>
  </div>
</template>

<script>
import Expenditure from "./reusables/expenditure.vue";
import ExpenditureTable from "./reusables/expenditureTable.vue";
import GeneralRemark from "./reusables/generalRemark.vue";
export default {
  components: {
    Expenditure,
    ExpenditureTable,
    GeneralRemark,
  },
  data() {
    return {
      tab: "expenditure",
    };
  },
};
</script>

<style>
</style>