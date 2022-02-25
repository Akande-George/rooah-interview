<template>
  <div>
    <q-table
      :rows="rows"
      table-class="text-grey"
      table-header-class="bg-blue-grey-10 text-white"
      :columns="columns"
      hide-pagination
      row-key="name"
    >
      <template v-slot:body="props">
        <q-tr :props="props">
          <q-td key="item" :props="props">
            {{ props.row.item }}
          </q-td>
          <q-td key="amount" :props="props">
            {{ props.row.amount }}
          </q-td>
          <q-td key="used" :props="props">
            <q-input outlined v-model="props.row.used" dense />
          </q-td>
          <q-td key="description" :props="props">
            {{ props.row.description }}
          </q-td>
          <q-td key="remark" :props="props">
            <q-input outlined v-model="props.row.remark" dense />
          </q-td>
        </q-tr>
      </template>
      <template v-slot:bottom-row>
        <q-tr v-if="addNew">
          <q-td><q-input outlined v-model="form.item" dense /></q-td>
          <q-td
            ><q-input outlined type="number" v-model="form.amount" dense
          /></q-td>
          <q-td
            ><q-input outlined type="number" v-model="form.used" dense
          /></q-td>
          <q-td><q-input outlined v-model="form.description" dense /></q-td>
          <q-td><q-input outlined v-model="form.remark" dense /></q-td>
        </q-tr>
        <q-tr>
          <q-td colspan="100%">
            <q-btn
              v-if="!addNew"
              outline
              color="primary"
              @click="addNew = !addNew"
              no-caps
              label="Add new expenditure"
            />
            <q-btn
              v-if="addNew"
              outline
              color="primary"
              no-caps
              @click="addExpenditure()"
              label="Add new expenditure"
            />
          </q-td>
        </q-tr>
      </template>
      <template v-slot:bottom>
        <div>
          Total: <span>{{ total }}</span>
        </div>
      </template>
    </q-table>
  </div>
</template>

<script>
const columns = [
  {
    name: "item",
    required: true,
    label: "ITEM",
    align: "left",
    field: (row) => row.item,
    sortable: true,
  },
  {
    name: "amount",
    align: "left",
    label: "AMOUNT (N)",
    field: "amount",
    sortable: true,
  },
  {
    name: "used",
    align: "left",
    label: "USED EXPENDITURE (N)",
    field: "used",
    sortable: true,
  },
  {
    name: "description",
    align: "left",
    label: "DESCRIPTION",
    field: "description",
    sortable: true,
  },
  {
    name: "remark",
    align: "left",
    label: "REMARK",
    field: "remark",
    sortable: true,
  },
];

const rows = [
  {
    item: "Printer Inc",
    amount: 2000,
    used: 0,
    description: "Project sample description",
    remark: "",
  },
  {
    item: "Card printing",
    amount: 600,
    used: 0,
    description: "ilum expedita debi",
    remark: "",
  },
];

import { useQuasar } from "quasar";
export default {
  data() {
    const $q = useQuasar();
    return {
      addNew: false,
      columns,
      rows,
      total: null,
      form: {
        item: "",
        amount: 0,
        used: 0,
        description: "Description",
        remark: "",
      },
      successNotify() {
        $q.notify({
          message: "Expenditure was added successfully!",
          icon: "check_circle",
          color: "green",
        });
      },
      failureNotify() {
        $q.notify({
          message: "Please put in an amount",
          icon: "block",
          color: "orange",
        });
      },
    };
  },

  methods: {
    addExpenditure() {
      if (this.form.amount) {
        this.form.amount = parseInt(this.form.amount);
        console.log(this.form);
        this.rows.push(this.form);
        this.form = {};
        this.addNew = false;
        this.calculateTotal();
        this.successNotify();
      } else {
        this.failureNotify();
      }
    },

    calculateTotal() {
      const arrayAmount = this.rows.map((element) => {
        return element.amount;
      });
      console.log("list", arrayAmount);
      this.total = arrayAmount.reduce((a, b) => a + b, 0);
    },
  },

  mounted() {
    this.calculateTotal();
  },
};
</script>

<style>
</style>