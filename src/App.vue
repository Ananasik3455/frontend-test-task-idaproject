<template>
  <div id="app">
    <Header
      @sorting="sortItems"
    />
    <Form
      @addproduct="addProduct"
    />
    <Content 
      :items="products"
      :sorting="sortValue"
      />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Form from './components/Form.vue';
import Content from './components/Content.vue';

export default {
  name: 'App',

  components: {
    Content,
    Header,
    Form,
  },

  data: () => ({
    products: [],
    sorting: '',
  }),

  methods: {
    addProduct(item) {
      this.products.push(item);
    },

    sortItems(item) {
      this.sorting = item;
    },

    
  },

  computed: {
    sortValue() {
      return this.sorting;
    }
  },
}
</script>

<style  lang="scss">
  @import "./style/main.scss";
</style>
