<template>
    <div id="carousel_pagination">
        <div
            v-for="index in props.length"
            :key="index"
            class="carousel_pagination_item"
            :class="{
                carousel_pagination_item_active: currentSlide === index - 1,
            }"
        ></div>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    set: Function;
    currentSlide: number;
    length: number;
}>();
</script>

<style lang="scss">
#carousel_pagination {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    padding: 20px 0px;
}

.carousel_pagination_item {
    background: $gray-color !important;
    border-radius: 100%;
    height: 10px;
    width: 10px;
    transition: all 0.5s;
}

.carousel_pagination_item_active {
    background: $primary-color !important;
    transform: scale(1.5);
}
</style>