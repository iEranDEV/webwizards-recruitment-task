<template>
    <div id="gallerySection">
        <h1>GALERIA</h1>
        <SectionGalleryCarousel />
    </div>
</template>

<style lang="scss">
#gallerySection {
    background-color: $white-color;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    flex-direction: column;
    padding-top: 100px;

    @include md {
        height: 100lvh;
    }
}
</style>