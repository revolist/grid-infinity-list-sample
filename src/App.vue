<template>
  <v-grid
    class="list"
    theme="compact"
    resize="false"
    readonly="true"
    :source="rows"
    :columns="columns"
  ></v-grid>
</template>

<script>
import VGrid from "@revolist/vue-datagrid";

function generateFakeDataRows(rowsNumber) {
  const result = [];
  const all = rowsNumber;
  for (let j = 0; j < all; j++) {
    let row = j;
    if (!result[row]) {
      result[row] = {};
    }
    result[row]["myRow"] = `I am row ${row}`;
  }
  return result;
}

export default {
  name: "App",
  data() {
    return {
      rows: generateFakeDataRows(10000),
      columns: [
        {
          prop: "myRow",
        },
      ],
    };
  },
  components: {
    VGrid,
  },
};
</script>

<style>
html,
body {
  height: 100%;
  padding: 0;
  margin: 0;
}
.list .row {
  display: flex;
}

.list .row .data-cell,
.data-header-cell {
  position: relative !important;
  width: auto !important;
}

revogr-focus,
.selection-border-range,
.edit-input-wrapper {
  width: 100% !important;
}
.header-wrapper {
  display: none;
}
</style>
