<template>
    <div id="carouselPagination">
        <div
            v-for="index in props.length"
            :key="index"
            class="carouselPaginationItem"
            @click="set(index - 1)"
            :class="{
                carouselPaginationItemActive: currentSlide === index - 1,
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
#carouselPagination {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    padding: 20px 0px;
}

.carouselPaginationItem {
    background: $gray-color !important;
    border-radius: 100%;
    height: 10px;
    width: 10px;
    transition: all 0.5s;
}

.carouselPaginationItemActive {
    background: $primary-color !important;
    transform: scale(1.5);
}
</style>