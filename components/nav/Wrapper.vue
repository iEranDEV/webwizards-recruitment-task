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
                <NavItem name="START" link="#startSection" />
                <NavItem name="O MNIE" link="#aboutSection" />
                <NavItem name="GALERIA" link="#gallerySection" />
                <NavItem
                    name="KONTAKT"
                    @click="isContactExpanded = !isContactExpanded"
                />
            </div>

            <!-- Social icons -->
            <div id="socialIcons">
                <img src="/social/facebook.svg" alt="To go facebook" />
                <img src="/social/instagram.svg" alt="To go instagram" />
                <img src="/social/youtube.svg" alt="To go youtube" />
            </div>
        </div>

        <!-- Toggler -->
        <div @click="isExpanded = !isExpanded" id="toggler">
            <X v-if="isExpanded" />
            <Menu v-else />
        </div>

        <!-- Contact modal -->
        <ModalContact v-if="isContactExpanded" :close="closeContactModal" />
    </nav>
</template>

<script setup lang="ts">
import { Menu, X } from "lucide-vue-next";
import { ref } from "vue";

const isExpanded = ref(false);
const isContactExpanded = ref(false);

const closeContactModal = () => {
    isContactExpanded.value = false;
};
</script>

<style lang="scss">
#navBar {
    background-color: $white-color;
    z-index: 2000;
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
    gap: 5px;

    @include xl {
        gap: 20px;
    }

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

#socialIcons {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 20px 0px;

    @include lg {
        margin: 0px 0px;
    }
}
</style>