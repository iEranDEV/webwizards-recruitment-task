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
            background: 'url(' + props.path + ')',
        }"
    ></div>
</template>

<script setup lang="ts">
const props = defineProps<{
    path: string;
    index: number;
    currentSlide: number;
}>();

const calcGap = () => {
    const val = props.index - props.currentSlide;

    if (val < 0) return "-" + Math.abs(val) * 75;
    return "+" + val * 75;
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
    z-index: 40;
    overflow: hidden;
    transition: all 1s;
    background-position: center !important;
    background-repeat: no-repeat !important;
    background-size: cover !important;
}
</style>