<template>
    <div id="app-wrapper">
        <!-- NavBar -->
        <NavWrapper />

        <!-- Start section -->
        <SectionStart />

        <!-- About section -->
        <SectionAbout />

        <!-- Gallery section -->
        <SectionGallery />
    </div>
</template>


<style lang="scss">
@import url("@/assets/css/global.scss");

#app-wrapper {
    display: flex;
    flex-direction: column;
    position: relative;
}
</style>