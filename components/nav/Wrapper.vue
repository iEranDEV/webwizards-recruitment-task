<template>
    <nav id="navBar">
        <!-- Logo -->
        <img id="logo" src="/logo.svg" alt="Logo" />

        <!-- Wrapper (links & socials) -->
        <div
            id="navBarWrapper"
            :style="{ maxHeight: isExpanded ? '1000px' : '0px' }"
        >
            <!-- Links -->
            <div id="navBarItems">
                <NavItem name="START" link="#start_section" />
                <NavItem name="O MNIE" link="#about_section" />
                <NavItem name="GALERIA" link="#gallery_section" />
                <NavItem name="KONTAKT" @click="test" />
            </div>

            <!-- Social icons -->
            <p>icons</p>
        </div>

        <!-- Toggler -->
        <div @click="isExpanded = !isExpanded" id="toggler">
            <X v-if="isExpanded" />
            <Menu v-else />
        </div>
    </nav>
</template>

<script setup lang="ts">
import { Menu, X } from "lucide-vue-next";
import { ref } from "vue";

const test = () => {
    console.log("test");
};

const isExpanded = ref(false);
</script>

<style lang="scss">
#navBar {
    background-color: $white-color;
    z-index: 50;
    padding: 0px 20px;
    height: 100px;
    width: 100%;
    gap: 40px;
    border-bottom: 4px solid $primary-color;
    display: flex;
    align-items: center;
    position: fixed;
    top: 0px;
    justify-content: space-between;

    @include xl {
        padding: 0px 140px;
    }
}

#navBarWrapper {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: auto;
    max-height: auto;

    @media screen and (max-width: 1024px) {
        position: absolute;
        background-color: $white-color;
        bottom: 0px;
        border-bottom: 4px solid $primary-color;
        overflow: hidden;
        left: 0px;
        transition: max-height 1s;
        max-height: 0px;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        transform: translateY(100%);
    }

    @include lg {
        display: flex;
    }
}

.expanded {
    height: auto !important;
}

#navBarItems {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;

    @media screen and (max-width: 1024px) {
        flex-direction: column;
    }
}

#logo {
    height: 50px;
    font-family: "Montserrat", sans-serif;
}

#toggler {
    display: block;
    display: flex;
    justify-content: center;
    align-content: center;
    cursor: pointer;

    @include lg {
        display: none;
    }
}
</style>