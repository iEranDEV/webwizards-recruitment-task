<template>
    <div id="carouselWrapper">
        <!-- Carousel slider element -->
        <div
            @touchstart="handleTouchStart"
            @touchmove="handleTouchMove"
            @touchend="handleTouchEnd"
            id="carousel"
        >
            <!-- Slides -->
            <div id="slider">
                <!-- Previous slide -->
                <div
                    @touchend.stop
                    @touchstart.stop
                    @click.prevent="move(-1)"
                    id="prevSlide"
                    :class="{ 'active-arrow': currentSlide - 1 >= 0 }"
                >
                    <ChevronLeft :size="48" />
                </div>

                <!-- Images -->
                <SectionGalleryCarouselItem
                    v-for="(slide, index) in slides"
                    :key="slide"
                    :path="slide"
                    :index="index"
                    :currentSlide="currentSlide"
                />

                <!-- Next slide -->
                <div
                    @touchend.stop
                    @touchstart.stop
                    @click.prevent="move(1)"
                    id="nextSlide"
                    :class="{
                        'active-arrow': currentSlide < slides.length - 1,
                    }"
                >
                    <ChevronRight :size="48" />
                </div>
            </div>
        </div>

        <!-- Carousel pagination -->
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

// List of slides (images in carousel)
const slides = [
    "/slides/slide1.png",
    "/slides/slide2.png",
    "/slides/slide3.png",
    "/slides/slide4.png",
];

// State variables
const currentSlide = ref(0);
const touchPosX = ref({
    start: 0,
    last: 0,
});

// Handle touchstart event (save x cord of touch)
const handleTouchStart = (e: TouchEvent) => {
    touchPosX.value = {
        start: e.touches[0].clientX,
        last: e.touches[0].clientX,
    };
};

// Handle touchmove event (update x cord of last touch)
const handleTouchMove = (e: TouchEvent) => {
    touchPosX.value.last = e.touches[0].clientX;
};

// Handle touchend event (end of swipe)
const handleTouchEnd = (e: TouchEvent) => {
    if (touchPosX.value.start > touchPosX.value.last) {
        move(1);
    } else {
        move(-1);
    }
};

// Set current slide for specific number
const set = (val: number) => {
    currentSlide.value = val;
};

// Move carousel by number of slides
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
    margin-top: 20px;
    width: 100%;
    aspect-ratio: 2/1;
}

#carousel {
    display: flex;
    width: 100%;
    height: 100%;
    align-items: center;
    overflow: hidden;
    justify-content: center;
    align-items: center;

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
    width: 100%;
    aspect-ratio: 2/1;

    @include md {
        width: auto;
        height: 100%;
        grid-area: 1 / 2 / 2 / 12;
    }
}

.active-arrow {
    color: $primary-color !important;
}

#prevSlide,
#nextSlide {
    align-items: center;
    color: $gray-color;
    position: absolute;
    z-index: 50;
    top: 50%;
    transform: translateY(-50%);
    border-radius: 90%;
    display: flex;
    align-items: center;
    cursor: pointer;
}

#prevSlide {
    left: 10px;

    @include md {
        left: 0px;
        transform: translateX(-100%);
    }
}

#nextSlide {
    right: 10px;

    @include md {
        right: 0px;
        transform: translateX(100%);
    }
}
</style>