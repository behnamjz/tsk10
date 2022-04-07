<template>
    <div>
        <button :class="`font-bold-14 ${type}-button`" @click="$emit('click')">
            {{text}}
            <div v-if="showIcon" class="icon">
                +
            </div>
        </button>
    </div>
</template>
<script>
export default {
    name: "Button",
    props: {
        showIcon: {
            default: false,
            type: Boolean
        },
        text: {
            default: '',
            type: String
        },
        type: {
            default: 'primary',
            type: String  
        }
    }
}
</script>

<style lang="scss" scoped>
@import "~/src/assets/sass/variable";

button {
    padding: $base-size - 2 $base-size + 4 ;
    display: flex;
    align-items: center;
    border-radius: $base-size * 4;
}

.primary-button {
    background: $color-blue;
    color: $color-white;
    border: none;

    & .icon {
        background: $color-white;
        color: $color-blue;
        border-radius: $base-size * 4;
        width: round($base-size * 1.4);
        height: round($base-size * 1.4);
        margin-left: round($base-size / 1.4);
        line-height: round($base-size * 1.4);
    }

    &:hover {
        box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.15);
    }

    &:active {
        background: $color-dark-blue;
    }
}

.secondary-button {
    background: $color-white;
    color: $color-black;
    border: 1px solid $color-light-gray;

    &:hover {
        border: 1px solid $color-gray;
    }

    &:active {
        background: $color-light-gray;
        color: $color-white;
    }

    & .icon {
        color: $color-black;
        border-radius: $base-size * 4;
        width: round($base-size * 1.4);
        height: round($base-size * 1.4);
        margin-left: round($base-size / 1.4);
        line-height: round($base-size * 1.4);
    }
}
</style>