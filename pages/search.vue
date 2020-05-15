<template>
  <div class="container">
    <div>
      {{$store.state.navbar.app[0]}}
      <ul>
        <li v-for="(item,idx) in list" :key="idx">{{item}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
import axios from 'axios'
export default {
  layout: "search",
  components: {
    Logo
  },
  data() {
    return {
      list: []
    };
  },
  async asyncData() {
    let {
      status,
      data: { list }
    } = await axios.get("http://localhost:3000/city/list");
    if (status == 200) {
      //不能用this 因为还没渲染
      return {list}
    }
  },
  // async mounted() {
  //   let self = this;
  //   let {
  //     status,
  //     data: { list }
  //   } = await axios.get("/city/list");
  //   if (status == 200) {
  //     self.list = list;
  //   }
  // },
  methods: {}
};
</script>

<style>
</style>
