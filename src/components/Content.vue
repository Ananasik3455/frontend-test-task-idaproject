<template>
  <main 
    class="content"
  >
    <product
      v-for="item in sortedItems"
      :key="item.id"
      :product="item"
      @removeItem="removeItem"
    />
  </main>  
</template>

<script>
import Product from './Product.vue';

export default {
  props: {
    items: Array,
    sorting: String,
  },
  components: {
    Product,
  },

  methods: {
    /**
     * Удаление товара по ID
     */
    removeItem(id) {
      console.log(id);
      this.items.forEach((item, index) => {
        if (item.id == id) {
          this.items.splice(index, 1);
          return;
        }
      })
    },
  },

  computed: {
    sortedItems() {
      let items = [...this.items];
      switch (this.sorting) {
        case 'default': {
          return items;
        }
        case 'higher': {
          return items.sort((a, b) => a.productPrice - b.productPrice);
        }
        case 'lower': {
          return items.sort((a, b) => b.productPrice - a.productPrice);
        }
        case 'byName': {
          return items.sort((a, b) => a.productName.toLowerCase() - b.productName.toLowerCase());
        }
        default: {
          return items;
        }
      }
    }
  },
}
</script>

