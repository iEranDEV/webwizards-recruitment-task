<template>
    <div
        class="slide"
        :style="{
            transform:
                'translateX(' +
                (props.index - props.currentSlide) * 100 +
                '%) translateX(' +
                calcGap() +
                'px)',
        }"
    >
        <img class="slide_img" :src="props.path" alt="Slide" />
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    path: string;
    index: number;
    currentSlide: number;
}>();

const calcGap = () => {
    const val = props.index - props.currentSlide;

    if (val < 0) return "-" + Math.abs(val) * 100;
    return "+" + val * 100;
};
calcGap();
</script>

<style lang="scss">
.slide {
    position: absolute;
    height: 100%;
    width: 100%;
    top: 0px;
    left: 0px;
    background: green;
    overflow: hidden;
    transition: all 1s;
}
.slide_img {
    width: 100%;
}
</style>