<template>
    <div class="input-field">
        <label class="title font-reg-14" v-if="showTitle">{{title}}</label>
        <div class="input">
            <input v-if="showButton" v-model="field" type="text" :placeholder="placeholder" @keyup.enter="AddToList">
            <input v-else type="text" :placeholder="placeholder" @input="handleInput">
            <button v-if="showButton" class="font-bold-14" :class="{'has-value': field}" :disabled="!field" @click="AddToList">Add +</button>
        </div>
        <Tag :Tags="list" showButton />
    </div>
</template>
<script>
import Tag from './Tag.vue'

export default {
    name: "Input",
    data() {
        return {
            field: null,
            list: []
        }
    },
    components: {Tag},
    props: {
        showButton: {
            default: false,
            type: Boolean
        },
        placeholder: {
            default: '',
            type: String
        },
        title: {
            default: 'title',
            type: String
        },
        showTitle: {
            default: false,
            type: Boolean
        }
    },
    methods: {
        AddToList() {
            // if has button //
            if (this.showButton) {
                this.list.push(this.field)
                this.field = null
                this.$emit('input', this.list)
            } 
        },
        handleInput (e) {
            this.$emit('input', e.target.value)
        }
    }
}
</script>

<style lang="scss" scoped>
@import "~/src/assets/sass/variable";
.input-field {
    margin-bottom: round($base-size * 1.7);
}

.input {
    display: flex;
    background: $color-input-bakcground;
    border: 1px solid $color-light-gray;
    padding: $base-size / 2 $base-size;
    border-radius: $base-size / 2;
    margin-bottom: $base-size / 2;

    &:hover {
        border-color: $color-gray;
        background: $color-white;
    }

    & input[type="text"] {
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

    & .icon {
        margin-right: $base-size;
    }

    & button {
        color: $color-light-gray;
        background: none;
        border: none;
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