<template>
  <div class="col-full push-top">
    <h1>Welcome to the forum</h1>
    <CategoryList :categories="categories"/>
  </div>
</template>

<script>
import CategoryList from '@/components/CategoryList';

export default {
  name: "Home",

  components: {
    CategoryList
  },

  computed: {
    categories () {
      return Object.values(this.$store.state.categories)
    }
  },

  data() {
    return {
      categories: Object.values(sourceData.categories)
    }
  }
};
</script>