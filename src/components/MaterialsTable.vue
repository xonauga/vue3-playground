<template>
  <div class="table-container">
    <div class="function-container">
      <div class="search-container">
        <input type="text" placeholder="Suche" v-model="suche" />
      </div>
      <div class="sort-container">
        <i
          class="sort-icon"
          :class="sortIcon"
          v-on:click="onClickSort"
          style="margin-left: 20px"
        ></i>
      </div>
    </div>
    <table id="fl-table">
      <thead class="fl-table-header">
        <tr>
          <th>Material</th>
          <th>HTZ</th>
          <th>Benennung</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in materials" :key="item.matnr">
          <td>{{ item.matnr }}</td>
          <td v-text="item.htz"></td>
          <td>{{ item.ktxt }}</td>
        </tr>
      </tbody>
      <tfoot class="fl-table-footer">
        <tr>
          <td>
            {{ footerText }}
          </td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
import mockdata from '@/mockdata/materials_mock';

export default {
  name: 'MaterialsTable',
  props: {
    title: String,
  },
  data: () => {
    return {
      mockdata: {},
      suche: null,
      sortUp: true,
    };
  },
  computed: {
    materials() {
      let items = this.mockdata.items.slice();
      if (this.suche) {
        items = items.filter((mat) => {
          if (
            mat.matnr.includes(this.suche) ||
            mat.htz.includes(this.suche) ||
            mat.ktxt.includes(this.suche)
          ) {
            return true;
          }
          return false;
        });
      }
      return items;
    },
    footerText() {
      return `Anzahl: ${this.materials.length}`;
    },
    sortIcon() {
      return this.sortUp
        ? 'fa-solid fa-arrow-down-short-wide sort-icon-up'
        : 'fa-solid fa-arrow-down-wide-short sort-icon-down';
    },
  },
  methods: {
    onClickSort() {
      this.sortUp = !this.sortUp;
      this.mockdata.items.sort((i1, i2) => {
        if (this.sortUp) return i1.matnr > i2.matnr ? 1 : -1;
        else return i1.matnr > i2.matnr ? -1 : 1;
      });
    },
  },
  created() {
    this.mockdata = mockdata.materials;
  },
  mounted() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.table-container {
  margin: auto;
  margin-top: 20px;
  padding: 10px;
  width: 60%;
  border: thin solid #6884b1;
}

.function-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-bottom: 20px;
}

.search-container {
  text-align: start;
}

.sort-container {
  text-align: end;
  margin: auto 10px auto 0;
}

.search-container input {
  background-color: #4e6a97;
  border: none;
  padding: 0.5em;
  border-radius: 8px;
  color: #3fb883;
}
.search-container input::placeholder {
  color: #3fb883;
}

.search-container input:focus {
  color: #3fb883;
  outline: none;
}

#fl-table {
  border-radius: 20px;
  margin: auto;
  border-collapse: collapse;
  width: 100%;
}

#fl-table thead {
  border-bottom: thin solid #6884b1;
}

#fl-table td,
th {
  text-align: left;
  padding: 5px;
}

#fl-table > tbody tr:hover {
  background-color: #4e6a97;
}

.fl-table-footer {
  border-top: 1px solid #6884b1;
}

.sort-icon {
  cursor: pointer;
  font-size: 1.5em;
}

.sort-icon-up {
  color: #3992bb;
}
.sort-icon-down {
  color: #dd7e18;
}
</style>
