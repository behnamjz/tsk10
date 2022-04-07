<template>
  <div>
    <ul>
      <li v-for="(tag, index) in Tags" :key="index" class="tag">
        <button @click="deleteFromList(index)" v-if="showButton">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18.3 5.70997C17.91 5.31997 17.28 5.31997 16.89 5.70997L12 10.59L7.10997 5.69997C6.71997 5.30997 6.08997 5.30997 5.69997 5.69997C5.30997 6.08997 5.30997 6.71997 5.69997 7.10997L10.59 12L5.69997 16.89C5.30997 17.28 5.30997 17.91 5.69997 18.3C6.08997 18.69 6.71997 18.69 7.10997 18.3L12 13.41L16.89 18.3C17.28 18.69 17.91 18.69 18.3 18.3C18.69 17.91 18.69 17.28 18.3 16.89L13.41 12L18.3 7.10997C18.68 6.72997 18.68 6.08997 18.3 5.70997Z" fill="#323232"/>
            </svg>
        </button>
        <span class="font-reg-10">{{ tag }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    showButton: {
      default: false,
      type: Boolean
    },
    Tags: {
      default: null,
      type: Array
    }
  },
  methods: {
    deleteFromList(index) {
      this.Tags.splice(index, 1);
    }
  }
};
</script>
<style lang="scss" scoped>
@import "~/src/assets/sass/variable";
ul {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    padding: 0;
}

.tag {
    border: 1px solid $color-light-gray;
    color: $color-gray;
    display: flex;
    margin: 4px 4px 4px 0;
    padding: 7px 12px;
    position: relative;
    border-radius: 50px;


    & span {
        color: $color-gray;
    }

    & button {
        background: none;
        border: none;
        margin: 0 7px 0 0;
        padding: 0;
        
        & svg {
            width: 10px;
            height: 10px;
            display: inherit;

            & path {
                fill: $color-gray;
            }
        }
    }

    &:hover {
        border-color: $color-gray;
        button, span {
            color: $color-black;
        }

        svg {
            path {
                fill: $color-black;
            }
        }
    }
}
</style>