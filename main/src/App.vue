<template>
  <div id = "app">
    <Fio lastName = 'Орлов' firstName = 'Максим' middleName = 'Андреевич' > </Fio>
    <Vyatsu :results="results"></Vyatsu>
    <Register></Register>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import axios from 'axios';
import { Component } from 'vue-property-decorator';
import Fio from '../../fio/src/components/Fio.vue';
import Vyatsu from '../../vyatsu/src/components/Vyatsu.vue';
import Register from '../../register/src/components/register.vue';

// const url = 'https://new.vyatsu.ru/';
// const url = 'http://127.0.0.1:5500/main/src/components/8.Html';

const url = 'http://localhost:8081/admission/';

export default Vue.extend({
  name: 'App',
  components: {
    Fio,
    Vyatsu,
    Register,
  },
  data() {
    return { Fio, results: [] };
  },
  mounted() {
    axios
      .get(url)
      .then((response: any) => {
        console.log(response);
        this.results = response.data;
      })
      .catch((error: any) => console.log(error));
  },
});
</script>
