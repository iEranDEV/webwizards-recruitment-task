<template>
    <div id="carouselWrapper">
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
const touchStartPosX = ref(0);

const set = (val: number) => {
    currentSlide.value = val;
};

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
#carouselWrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;

    @include xl {
        width: 100%;
        height: 75%;
    }
}

#carousel {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    width: 100%;
    height: 100%;
    overflow: hidden;

    @include md {
        padding: 0px 20px;
    }

    @include lg {
        padding: 0px 70px;
    }

    @include xl {
        padding: 0px 140px;
    }
}
#slider {
    position: relative;
    grid-area: 1 / 2 / 2 / 12;
    aspect-ratio: 2/1;
}

.active-arrow {
    color: $primary-color !important;
}

#prevSlide,
#nextSlide {
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    color: $gray-color;
}

#prevSlide {
    grid-area: 1 / 1 / 2 / 2;
    justify-content: end;
}

#nextSlide {
    grid-area: 1 / 12 / 2 / 13;
    justify-content: start;
}
</style>