<template>
  <div class="col-full push-top">

    <h1>Create new thread in <i>{{forum.name}}</i></h1>

    <form @submit.prevent="save">
      <div class="form-group">
        <label for="thread_title">Title:</label>
        <input v-model="title" type="text" id="thread_title" class="form-input" name="title">
      </div>

      <div class="form-group">
        <label for="thread_content">Content:</label>
        <textarea v-model="text" id="thread_content" class="form-input" name="content" rows="8" cols="140"></textarea>
      </div>

      <div class="btn-group">
        <button @click.prevent="cancel" class="btn btn-ghost">Cancel</button>
        <button class="btn btn-blue" type="submit" name="Publish">Publish </button>
      </div>
    </form>
  </div>
</template>

<script>
    export default {
      props: {
        forum: {
          type: Object,
          required: true
        }
      },
      data () {
        return {
          title: '',
          text: ''
        }
      },
      methods: {
        save () {
          this.$store.dispatch('createThread', {
            forumId: this.forum['.key'],
            title: this.title,
            text: this.text
          }).then(thread => {
            this.$router.push({name: 'ThreadShow', params: {id: thread['.key']}})
          })
        },
        cancel () {
          this.$router.push({name: 'Forum', params: {id: this.forum['.key']}})
        }
      }
    }
</script>

<style scoped>
</style>