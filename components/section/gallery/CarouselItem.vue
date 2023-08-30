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
    >
        <!--<img class="slideImg" :src="props.path" alt="Slide" />-->
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
    background-position: center !important;
    background-repeat: no-repeat !important;
    background-size: cover !important;
}
.slideImg {
    width: 100%;
}
</style>