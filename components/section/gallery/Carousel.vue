<template>
    <div id="carousel_wrapper">
        <div id="carousel">
            <div
                id="prevSlide"
                :class="{ 'active-arrow': currentSlide - 1 >= 0 }"
            >
                <ChevronLeft @click="move(-1)" :size="48" />
            </div>
            <div id="slider">
                <SectionGalleryCarouselItem
                    v-for="(slide, index) in slides"
                    :key="slide"
                    :path="slide"
                    :index="index"
                    :currentSlide="currentSlide"
                />
            </div>
            <div
                id="nextSlide"
                :class="{ 'active-arrow': currentSlide < slides.length - 1 }"
            >
                <ChevronRight @click="move(1)" :size="48" />
            </div>
        </div>
        <SectionGalleryPagination
            :currentSlide="currentSlide"
            :set="set"
            :length="slides.length"
        />
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { ChevronRight, ChevronLeft } from "lucide-vue-next";

const slides = [
    "/slides/slide1.png",
    "/slides/slide2.png",
    "/slides/slide3.png",
    "/slides/slide4.png",
];

const currentSlide = ref(2);

const move = (val: number) => {
    if (
        currentSlide.value + val >= 0 &&
        currentSlide.value + val <= slides.length - 1
    ) {
        currentSlide.value = currentSlide.value + val;
    }
};
</script>

<style lang="scss">
#carousel_wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    height: 75%;
}
#carousel {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    width: 100%;
    height: 100%;
    overflow: hidden;

    @include lg {
        padding: 0px 140px;
    }
}
#slider {
    position: relative;
    height: 100%;
    grid-area: 1 / 2 / 2 / 12;
}

.active-arrow {
    color: $primary-color !important;
}

#prevSlide,
#nextSlide {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: $gray-color;
}

#prevSlide {
    grid-area: 1 / 1 / 2 / 2;
}

#nextSlide {
    grid-area: 1 / 12 / 2 / 13;
}
</style>