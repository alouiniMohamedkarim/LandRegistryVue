<template>
  <div class="vuestic-feed">
    <div v-if="posts.length == 0" class="empty">Your feed is empty.</div>
    <div class="post" v-for="post in posts" :class="{last: posts.indexOf(post) === posts.length - 1}">

      <div class="underscored">
        <span class="text"><span class="name">{{post.info._id}}</span> </span>

      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'vuestic-feed',
    props: ['initialPosts'],
    data () {
      return {
        posts: this.initialPosts
      }
    },

  }
</script>

<style lang="scss">
  @import "../../../sass/variables";

  .vuestic-feed {
    padding-top: .5rem;
    padding-bottom: .5rem;
    padding-left: 1.5rem;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    .empty {
      text-align: center;
    }
    .post {
      display: flex;
      justify-content: space-between;
      align-items: center;
      .photo-container {
        margin-right: 1rem;
        border-radius: 50%;
        border: 2px solid $lighter-gray;
        .photo {
          background-size: cover !important;
          width: 3rem;
          height: 3rem;
          border-radius: 50%;
        }
      }
      .underscored {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        border-bottom: $light-gray2 2px solid;
        overflow: hidden;
        padding-right: 0.7rem;
        height: 3.5rem;
        .text {
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          .name {
            font-weight: $font-weight-bold;
          }
        }
        .close-btn {
          margin-left: 1rem;
          i {
            left: 10.5px;
          }
        }
      }
      &.last {
        .underscored {
          border-bottom: none;
        }
      }
    }
  }
</style>
