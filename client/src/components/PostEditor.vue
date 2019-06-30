<template>
    <form @submit.prevent="addPost">
      <div class="form-group">
        <textarea
          name=""
          id=""
          cols="30"
          rows="10"
          class="form-input"
          v-model="newPostText"
        ></textarea>
      </div>
      <div class="form-actions">
        <button class="btn-blue">Submit post</button>
      </div>
    </form>
</template>

<script>
export default {
    props: {
        threadId: {
            required: true
        }
    },
    data () {
        return {
            newPostText: ''
        }
    },

    methods: {
      addPost () {
        const postId = 'postNumber' + Math.random()
        const post = {
          text: this.newPostText,
          publishedAt: Math.floor(Date.now() / 1000),
          threadId: this.threadId,
          userId: 'jUjmgCurRRdzayqbRMO7aTG9X1G2',
          '.key': postId
        }
        /*this.$set(sourceData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourceData.users[post.userId].posts, postId, postId)*/
        this.newPostText = ''

        this.$emit('save-post', {post}) //так передается объект, если название перемнной и имени проперти совпадает, иначе {post: postName}
      }
    }
}
</script>

