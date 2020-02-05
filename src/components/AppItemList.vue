<template>
  <div>
    <h5>
      {{title}}
      <span class="badge badge-info">{{ names.length }}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="(name,index) in names" :key="name">
            <div class="row">
              <div class="col-md">{{name}}</div>
              <div class="col-md text-right">
                <button @click="removeName(index)" class="btn btn-info">
                  <span class="fa fa-trash"></span>
                </button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input
            type="text"
            class="form-control"
            v-model="name"
            @keyup.enter="addName(name)"
            :placeholder="inputName"
          />
          <div class="input-group-append">
            <button class="btn btn-info" @click="addName(name)">
              <span class="fa fa-plus"></span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppItemList',
  data() {
    return {
      title: 'Prefixos',
      names: ['Air', 'Jet', 'Sky'],
      name: null,
      inputName: 'Digite o prefixo'
    };
  },
  methods: {
    addName(name) {
      if (!name) return;
      this.names.push(name);
      //Dispatch an event
      const evt = new CustomEvent('MyEventType', { detail: this.name });
      window.dispatchEvent(evt);
      this.name = '';
    },
    removeName(index) {
      this.names.splice(index, 1);
    }
  }
};
</script>

<style>
</style>