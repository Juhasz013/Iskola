<template>
  <div class="d-flex flex-column container-fluid">
    <!-- Header -->
    <div class="d-flex justify-content-between mb-3">
      <h2>Kártyák</h2>
      <div>
        <div class="dropdown">
          kártya/odal:
          <select
            class="form-select"
            aria-label="Default select example"
            v-model="rowsPerPage">
            <option
              v-for="rowsnumber of rowsPerPageArray"
              :key="rowsnumber"
              :value="rowsnumber">
              {{ rowsnumber }}
            </option>
          </select>
        </div>
      </div>
    </div>
 
    <!-- Kártyák -->
    <div class="my-cards-height overflow-auto">
      <Cards :datas="datas" />
    </div>
 
    <!-- paginátor -->
    <div>
      <Paginator
        :currentPage="pageNumber"
        :totalPages="numberOfPages"
        @page-change="handlePageChange"
      />



    </div>
  </div>
</template>
 
<script>
import Cards from "@/components/Cards.vue";
import Paginator from "@/components/Paginator.vue";
import axios from "axios";
export default {
  components: {Cards, Paginator},
  props: ["url"],
  data() {
    return {
      datas: [],
      rowsPerPage: 5,
      pageNumber: 1,
      numberOfPages: 1,
      rowsPerPageArray: [1, 3, 5, 10, 25, 30],
    };
  },
  watch: {
    rowsPerPage() {
      this.pageNumber = 1;
      this.getDatas();
      this.getTotalPages()
    },
    
  },
  mounted() {
    this.getDatas();
    this.getTotalPages()
   
  },
  methods: {
    async getDatas() {
      const url = `${this.url}/queryOsztalynevsorLimit/${this.pageNumber}/${this.rowsPerPage}`;
      const response = await axios.get(url);
      this.datas = response.data.data;
      console.log(this.datas);
    },
    handlePageChange(page) {
      this.pageNumber = page;
      this.getDatas();
    },
    async getTotalPages() {
      const url = `${this.url}/queryHanyOldalVan/${this.rowsPerPage}`;
      const response = await axios.get(url);
      this.numberOfPages = response.data.data.oldalszam;
      console.log(this.numberOfPages);
      
    },
  },
};
</script>
 
<style scoped>
.my-cards-height {
  height: calc(100vh - 260px);
}
</style>