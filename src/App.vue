<template>
  <b-container>
    <div v-if="formFlag">
      <List @click="ShowForm" :data="data.mockData" />
    </div>
    <div v-else>
      <Form @click="ShowForm" @AddPost="AddPost"/>
    </div>
  </b-container>
</template>

<script>
import List from '@/components/Pages/List.vue'
import Form from '@/components/Pages/PostForm.vue'
import mockData from './data.json'

export default {
  name: 'App',
  data() {
    return {
      formFlag: true,
      data: {mockData}
    }
  },
  components: {
    List,
    Form
  },
  methods: {
    ShowForm() {
      this.formFlag = !this.formFlag
    },
    AddPost(obj) {
      this.data.mockData.push(obj)
      this.formFlag = !this.formFlag
      
    }
  }
}
</script>

<style lang='scss'>
@import "~/src/assets/sass/variable";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
