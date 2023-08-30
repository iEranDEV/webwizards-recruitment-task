<template>
    <section id="startSection">
        <div id="heroImage"></div>
    </section>
</template>

<style lang="scss">
#heroImage {
    height: 700px;
    background-image: url("/hero_image.png");
    background-position: center;
    background-size: cover;

    @include xl {
        background-position: 50% calc(50% + 50px);
    }
}
</style>