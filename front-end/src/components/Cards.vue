<template>
    <div>
      <div class="row row-cols-1 row-cols-md-2 g-4 m-0">
        <div class="col" v-for="(data, index) in datas" :key="index">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">{{ data.nev }}</h5>
              <p class="card-text">
                  {{ data.osztalyNev }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
   
  <script>
  export default {
      props: ["datas"],
  };
  </script>
   
  <style>
  </style>