<template>
  <div class="flex-grid">
    <!--<UserProfileCard-->
      <!--:user="user"-->
      <!--:userPostsCount="userPostsCount"-->
      <!--:userThreadsCount="userThreadsCount"-->
    <!--/>-->
    <UserProfileCardEditor
      :user="user"
      :userPostsCount="userPostsCount"
      :userThreadsCount="userThreadsCount"
    />

    <div class="col-7 push-top">

      <div class="profile-header">
        <span class="text-lead">
            Joker's recent activity
        </span>
        <a href="#">See only started threads?</a>
      </div>

      <hr>
      <PostList :posts="userPosts"/>
    </div>
  </div>
</template>

 <script>
    import PostList from '@/components/PostList'
    import UserProfileCardEditor from '@/components/UserProfileCardEditor'
    import UserProfileCard from '@/components/UserProfileCard'
    import {mapGetters} from 'vuex'
    import {countObject} from '@/utils/utils'
    export default {
      components: {
        PostList,
        UserProfileCard,
        UserProfileCardEditor
      },
       computed: {
        ...mapGetters({
          user: 'authUser'
        }),
         userThreadsCount () {
          return countObject(this.user.threads)
        },
         userPostsCount () {
          return countObject(this.user.posts)
        },
         userPosts () {
          if (this.user.posts) {
            return Object.values(this.$store.state.posts)
          }
          return []
        }
      }
    }
</script>

 <style scoped>
 </style>