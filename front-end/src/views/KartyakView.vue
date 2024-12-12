<template>
  <div>
    <div class="d-flex justify-content-between">
      <h2>Kártyák</h2>
      <div>
        <div class="">
          kártya/odal:
          <select
            class="form-select"
            aria-label="Default select example"
            v-model="rowsPerPage"
          >
            <option
              v-for="rowsnumber of rowsPerPageArray"
              :key="rowsnumber"
              :value="rowsnumber"
            >
              {{ rowsnumber }}
            </option>
          </select>
        </div>
      </div>
    </div>

     <!-- Kártyák -->
     <div>

    </div>

    <!-- Footer -->
    <!-- Ide megy a paginátor -->
    <div>
      <h4>Paginátor</h4>
    </div> 
  </div>
</template>

<script>
export default {
  props: ["url"],
  data() {
    return {
      datas: [],
      rowsPerPage: 5,
      rowsPerPageArray: [3, 5, 10, 30, 50],
    };
  },
};
</script>

<style></style>
