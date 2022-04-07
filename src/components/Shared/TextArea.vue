<template>
    <div class="textarea-field">
        <label for="textarea" class="title font-reg-14" v-if="showTitle">{{title}}</label>
        <div class="textarea">
            <textarea id="textarea" :placeholder="placeholder" @input="handleInput" />
        </div>
    </div>
</template>
<script>
export default {
    name: "Input",
    props: {
        title: {
            default: 'title',
            type: String
        },
        placeholder: {
            default: '',
            type: String
        },
        showTitle: {
            default: false,
            type: Boolean
        }
    },
    methods: {
        handleInput (e) {
            this.$emit('input', e.target.value)
        }
    }
}
</script>

<style lang="scss" scoped>
@import "~/src/assets/sass/variable";

.textarea-field {
    margin-bottom: round($base-size * 1.7);
}

.textarea {
    display: flex;
    background: $color-input-bakcground;
    border: 1px solid $color-light-gray;
    padding: $base-size / 2 $base-size;
    border-radius: $base-size / 2;

    &:hover {
        border-color: $color-gray;
        background: $color-white;
    }

    & textarea {
        flex: 1 1 auto;
        border: none;
        background: none;

        &::placeholder {
            color: $color-gray;
        }
        &:focus {
            outline: none;
        }
    }

    & label {
        color: $color-gray;
    }

    & .has-value {
        color: $color-blue;
        svg {
            path {
                fill: $color-black;
            }
        }
    }
}

.title {
    padding: 0 10px;
}
</style>