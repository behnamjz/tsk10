<template>
    <div class="input-field">
        <div class="input" :class="{'has-icon': showIcon}">
            <div v-if="showIcon" class="icon" :class="{'has-value': field}">
                <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12.5 11H11.71L11.43 10.73C12.63 9.33 13.25 7.42 12.91 5.39C12.44 2.61 10.12 0.39 7.32001 0.05C3.09001 -0.47 -0.469985 3.09 0.0500152 7.32C0.390015 10.12 2.61002 12.44 5.39002 12.91C7.42002 13.25 9.33001 12.63 10.73 11.43L11 11.71V12.5L15.25 16.75C15.66 17.16 16.33 17.16 16.74 16.75C17.15 16.34 17.15 15.67 16.74 15.26L12.5 11ZM6.50002 11C4.01002 11 2.00002 8.99 2.00002 6.5C2.00002 4.01 4.01002 2 6.50002 2C8.99002 2 11 4.01 11 6.5C11 8.99 8.99002 11 6.50002 11Z" fill="#9D9D9D"/>
                </svg>
            </div>
            <input v-model="field" type="text" :placeholder="placeholder" @input="$emit('filter', field)">
        </div>
    </div>
</template>
<script>
export default {
    name: "SearchInput",
    data() {
        return {
            field: null
        }
    },
    props: {
        showIcon: {
            default: false,
            type: Boolean
        },
        placeholder: {
            default: '',
            type: String
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

    & .icon {
        margin-right: $base-size;
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

.has-icon {
    border-radius: $base-size * 3;
}
</style>