<template>
  <div class="post">
    <div class="user-info">
      <a href="#" class="user-name">{{user.name}}</a>

      <a href="#">
        <img class="avatar-large" :src="user.avatar" alt>
      </a>

      <p class="desktop-only text-small">{{userPostsCount}} posts</p>
    </div>

    <div class="post-content">
      <div>{{post.text}}</div>
    </div>

    <div class="post-date text-faded">
      <BaseDate :timestamp="post.publishedAt" />
    </div>
  </div>
</template>

<script>
import {countObject} from '@/utils/utils'
export default {
  props: {
    post: {
      required: true,
      type: Object
    }
  },
  computed: {
    user() {
      return this.$store.state.users[this.post.userId];
    },
    userPostsCount() {
      return countObject(this.user.posts);
    }
  }
};
</script>

