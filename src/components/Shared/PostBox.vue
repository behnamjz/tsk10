<template>
  <div class="box" v-if="post">
      <img :src="post.cover" alt="post.title" class="cover" />
      <div class="detail">
        <h2 class="font-bold-18">
          {{post.title}}
        </h2>
        <h3 class="font-reg-14">
          {{post.description}}
        </h3>
        <Tag :Tags="post.tags" />
      </div>
    <div class="meta">
      <img src="https://picsum.photos/600/300/?image=25" alt="post.title" class="avatar" />
      <div class="author">
        <h4 class="font-bold-10">{{post.author}}</h4>
        <h5 class="font-reg-10">{{post.date}}</h5>
      </div>
      <div class="favorite">
        <button @click="like">
          <svg width="14" height="12" viewBox="0 0 14 12" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M12.1066 0.659993C10.3466 -0.540006 8.17331 0.0199936 6.99998 1.39333C5.82665 0.0199936 3.65331 -0.546673 1.89331 0.659993C0.959979 1.29999 0.373313 2.37999 0.333313 3.51999C0.239979 6.10666 2.53331 8.17999 6.03331 11.36L6.09998 11.42C6.60665 11.88 7.38665 11.88 7.89331 11.4133L7.96665 11.3467C11.4666 8.17333 13.7533 6.09999 13.6666 3.51333C13.6266 2.37999 13.04 1.29999 12.1066 0.659993ZM7.06665 10.3667L6.99998 10.4333L6.93331 10.3667C3.75998 7.49333 1.66665 5.59333 1.66665 3.66666C1.66665 2.33333 2.66665 1.33333 3.99998 1.33333C5.02665 1.33333 6.02665 1.99333 6.37998 2.90666H7.62665C7.97331 1.99333 8.97331 1.33333 9.99998 1.33333C11.3333 1.33333 12.3333 2.33333 12.3333 3.66666C12.3333 5.59333 10.24 7.49333 7.06665 10.3667Z" fill="#9D9D9D"/>
          </svg>
        </button>
        <h5 class="font-reg-10">{{post.likeCount}}</h5>
      </div>
    </div>
</div>
</template>

<script>
import Tag from './Tag.vue'
export default {
  name: 'PostBox',
  components: {Tag},
  props: {
    post: Object,
    default: null
  },
  methods: {
    like() {this.post.likeCount += 1}
  }
}
</script>

<style lang="scss" scoped>
@import "~/src/assets/sass/variable";
.box {
    border: 1px solid $color-light-gray;
    border-radius: $base-size % 5;
    padding: round($base-size * .85);
    
    * {
      margin-bottom: round($base-size * .85);
    }

    .cover {
      height: 123px;
      width: 100%;
    }

    & h2 {
      color: $color-black;
    }

    & h3 {
      color: $color-gray;
    }

    .meta {
      display: flex;
      margin: 0 auto;

      .author {
        display: flex;
        flex-direction: column;
        flex: 3;
        margin: 0 auto;

        h4, h5 {
          padding: 0;
          margin-bottom: 4px;
        }

        h5 {
          color: $color-gray;
        }
      }

      .favorite {
        display: flex;
        flex: 1;
        flex-direction: row-reverse;
        align-items: center;
        color: $color-gray;
        margin: 0 auto;

        & button {
          background: none;
          border: none;
          height: $base-size;
          margin: 0 0 0 $base-size / 2;
          padding: 0;
        }

        h5 {
          color: $color-gray;
          padding: 0;
          margin: 0;
        }
      }

      .avatar {
        width: $base-size * 2;
        height: $base-size * 2;
        border-radius: $base-size * 2;
        margin: 0 $base-size / 2 0 0;
      }
    }

    .detail {
      min-height: 180px;
    }

    & button {
      &:active {
        svg {
          path {
            fill: red;
          }
        }
        & + .font-reg-10 {
          color: red;
        }
      }
    }
}
</style>
