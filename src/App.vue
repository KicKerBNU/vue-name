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
            <h5>
              Prefixes
              <span class="badge badge-info">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="(prefix,index) in prefixes" :key="prefix">  
                  <div class="row">
                    <div class="col-md">
                      {{prefix}}
                    </div>
                    <div class="col-md text-right">
                      <button class="btn btn-info" @click="removePrefix(index)"><span class="fa fa-trash"></span></button>
                    </div>
                  </div>
                    </li>
                </ul>
                <br />
                <div class="input-group">
                  <input type="text" class="form-control" v-model="prefix" @keyup.enter="addPrefix(prefix)"  placeholder="Digite o prefixo">
                  <div class="input-group-append">
                    <button class="btn btn-info" @click="addPrefix(prefix)">
                    <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="col md">
            <h5>
              Sufixes
              <span class="badge badge-info">{{ sufixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="(sufix,index) in sufixes" :key="sufix">
                    <div class="row">
                    <div class="col-md">
                      {{sufix}}
                    </div>
                    <div class="col-md text-right">
                      <button class="btn btn-info" @click="removeSufix(index)"><span class="fa fa-trash"></span></button>
                    </div>
                  </div>
                    
                    </li>
                </ul>
                <br />
                <div class="input-group">
                  <input type="text" class="form-control" v-model="sufix" @keyup.enter="addSufix(sufix)" placeholder="Digite o prefixo">
                  <div class="input-group-append">
                    <button class="btn btn-info" @click="addSufix()">
                    <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>

        </div>
        <br />
        <h5>
          Domains
          <span class="badge badge-info">{{ domains.length }}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="domain in domains" :key="domain.name">
                <div class="row">
                  <div class="col-md">
                    {{domain.name}}
                  </div>
                  <div class="col-md text-right">
                    <a class="btn btn-info" target="_blank" :href="domain.checkout">
                      <span class="fa fa-shopping-cart"></span>
                    </a>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";

export default {
	name: "app",
	data() {
		return {
      prefix: null,
      sufix: null,
			prefixes: ["Air", "Jet", "Sky"],
			sufixes: ["Hub", "Station", "Mart"],
		};
  },
  computed: {
    domains() {
      const domains = [];
      for(const prefix of this.prefixes) {
        for (const sufix of this.sufixes){
          const name = (prefix + sufix);
          const url = name.toLowerCase();
          const checkout = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com.br&_ga=2.43763173.1163398862.1580698604-1119943990.1580698604` 
          domains.push({
            name,
            checkout
          });
        }
      }
      return domains;
    }
  },
	methods: {
		addPrefix(prefix) {
      if(this.prefix.trim === "") return;
      this.prefixes.push(prefix);
      this.prefix = "";
		},
		addSufix(sufix) {
      if(this.sufix.trim === "") return;
      this.sufixes.push(sufix);
      this.sufix = "";
    },
    removePrefix(index){
      this.prefixes.splice(index,1);
    },
    removeSufix(index){
      this.sufixes.splice(index,1);
    }
	},
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
