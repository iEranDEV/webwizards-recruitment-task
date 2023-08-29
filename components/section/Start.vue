<template>
    <section id="start_section">
        <div id="hero_image"></div>
    </section>
</template>

<style lang="scss">
#hero_image {
    height: 700px;
    background-image: url("/hero_image.png");
    background-position: center;
    background-size: cover;

    @include xl {
        background-position: 50% calc(50% + 50px);
    }
}
</style>