<template>
  <div>
    <h5>
      {{title}}
      <span class="badge badge-info">{{domains.length}}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="domain in domains" :key="domain">
            <div class="row">
              <div class="col-md">{{domain}}</div>
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
</template>

<script>
export default {
  data() {
    return {
      title: 'Domains',
      domains: []
    };
  },
  mounted() {
    window.addEventListener(
      'MyEventType',
      evt => {
        console.log(evt.detail);
        this.domains.push(evt.detail);
      },
      false
    );
  },
  methods: {}
};
</script>

<style>
</style>