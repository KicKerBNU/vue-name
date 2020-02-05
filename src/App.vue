<template>
  <div>
    <div id="slogan">
      <div class="text-center">
        <h1>NameGator</h1>
        <br />
        <h6 class="text-secondary">Gerador de nomes utilizando Vue.js, GraphQL e Node</h6>
      </div>
    </div>

    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col md">
            <AppItemList ref="initialName"></AppItemList>
          </div>
          <div class="col md">
            <AppItemList ref="lastName"></AppItemList>
          </div>
        </div>
        <br />
        <Domains></Domains>
      </div>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css';
import 'font-awesome/css/font-awesome.css';
import AppItemList from './components/AppItemList';
import Domains from './components/Domains';
export default {
  name: 'app',
  components: {
    AppItemList,
    Domains
  },
  data() {
    return {
      sufix: null,
      sufixes: ['Hub', 'Station', 'Mart']
    };
  },
  mounted() {
    this.$refs.initialName.title = 'Prefix';
    this.$refs.lastName.title = 'Sufix';
    this.$refs.lastName.names = ['Hub', 'Station', 'Mart'];
    this.$refs.lastName.inputName = 'Digite o sufixo';
  },
  methods: {}
};
</script>

<style>
#slogan {
  margin-top: 30px 30px;
}
#main {
  background-color: #f1f1f1;
  padding: 30px 30px;
}
</style>
