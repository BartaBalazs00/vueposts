<template>
  <div>
      <div v-if="!edit">
        <h2>{{post.title}}</h2>
        <div>{{post.body}}</div>
        <button @click="Edit">Edit</button>
      </div>
      <div v-if="edit">
          <input type="text" v-model="title"><br>
          <input type="text" v-model="body"><br>
          <button @click="Save">Save</button>
      </div>
  </div>
</template>

<script>
export default {
    props: ['post'],
    data() {
        return {
            title: this.post.title,
            body: this.post.body,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('post-item-changed', {
                original: this.post,
                new: {
                    title: this.title,
                    body: this.body
                    },
            })
        }
    }
}
</script>

<style>
</style>