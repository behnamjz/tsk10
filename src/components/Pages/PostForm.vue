<template>
    <div>
      <b-row class="header">
        <b-col cols="4">
          <Button text="<" @click="$emit('click')" type="secondary" />
        </b-col>
        <b-col cols="8">
          <Button text="Publish Post" @click="AddPost" />
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="4">
          <Input title="Title" showTitle behnam="titleField" />
          <Textarea title="Description" showTitle v-model="descriptionField" />
          <Input title="Tags" showTitle showButton v-model="tagsArray"/>
        </b-col>
      </b-row>
    </div>
</template>

<script>
import Input from '@/components/Shared/Input.vue'
import Textarea from '@/components/Shared/TextArea.vue'
import Button from '@/components/Shared/Button.vue'

export default {
  name: 'PostForm',
  data() {
    return {
      titleField: null,
      descriptionField: null,
      tagsArray: [],
      monthNames: ["January", "February", "March", "April", "May", "June",
        "July", "August", "September", "October", "November", "December"
      ],
      today: new Date()
    }
  },
  components: {
    Input,
    Button,
    Textarea
  },
  methods: {
    AddPost() {
      const myData = {
        "title": this.titleField,
        "cover": "https://picsum.photos/600/300/?image=25",
        "description": this.descriptionField,
        "tags": this.tagsArray,
        "author": "Behnam Jaberi",
        "date": `${this.today.getDate()} ${this.monthNames[this.today.getMonth() + 1]} ${this.today.getFullYear()}`,
        "likeCount": 0
      }
      this.$emit('AddPost', myData)
    }
  }
}
</script>

<style lang='scss'>
@import "~/src/assets/sass/variable";

.header {
  padding: $base-size * 3 0 $base-size;
}

.col-3 {
  padding: 7px !important;
}

.col-8 {
  button {
    float: right;
  }
}
</style>
