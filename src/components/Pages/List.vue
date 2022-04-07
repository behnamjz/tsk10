<template>
    <div>
      <b-row class="header">
        <b-col cols="4">
          <Search placeholder="Search" showIcon @filter="filteredItems" />
        </b-col>
        <b-col cols="8">
          <Button text="Add New Post" @click="$emit('click')" showIcon />
        </b-col>
      </b-row>
      <div class="list">
        <PostBox v-for="(item, index) in filteredItem" :key="index" :post="item"/>
      </div>
    </div>
</template>

<script>
import PostBox from '@/components/Shared/PostBox.vue'
import Search from '@/components/Shared/Search.vue'
import Button from '@/components/Shared/Button.vue'

export default {
  name: 'ListPage',
  props:['data'],
  data() {
    return {
      filteredItem: this.data
    }
  },
  components: {
    PostBox,
    Search,
    Button
  },
  methods: {
    filteredItems(value) {
      if (value) {
        this.filteredItem = this.data.filter(item => {
          return item.title.toLowerCase().includes(value.toLowerCase()) || item.description.toLowerCase().includes(value.toLowerCase())
        })
      } else {
        this.filteredItem = this.data
      }
      
    }
  }
}
</script>

<style lang='scss' scoped>
@import "~/src/assets/sass/variable";

.header {
  padding: $base-size * 3 0 $base-size;
}

.list {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 1fr;
  grid-column-gap: $base-size / 2;
  grid-row-gap: $base-size;
}

.col-3 {
  padding: 7px !important;
}
</style>
