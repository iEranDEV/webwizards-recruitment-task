<template>
    <a v-if="link" :href="link" @click="scrollTo" class="nav-item">
        {{ name }}
    </a>
    <button v-else type="button" class="nav-item">
        {{ name }}
    </button>
</template>

<script setup lang="ts">
const props = defineProps<{
    name: string;
    link?: string;
}>();

const scrollTo = (e: MouseEvent) => {
    e.preventDefault();

    if (props.link) {
        document.querySelector(props.link)?.scrollIntoView({
            behavior: "smooth",
        });
    }
};
</script>

<style lang="scss">
.nav-item {
    all: unset;
    font-size: 12px;
    letter-spacing: 4.8px;
    border-radius: 21px;
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 0px 0px $white-color;
    padding: 0px 40px;
    color: $gray-color;
    cursor: pointer;
    transition: box-shadow 0.2s ease-in-out;

    &:hover {
        box-shadow: 0px 5px 10px $secondary-color;
    }
}
</style>