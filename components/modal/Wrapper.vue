<template>
    <div class="modalWrapper">
        <div class="modalBox">
            <slot></slot>
        </div>
    </div>
</template>

<style lang="scss">
.modalWrapper {
    height: 100lvh;
    width: 100lvw;
    position: fixed;
    z-index: 100;
    display: flex;
    justify-content: center;
    align-items: center;
    left: 0px;
    top: 0px;
}

.modalBox {
    background: $white-color;
    padding: 55px 20px 20px 20px;
    width: 90%;
    max-width: 530px;
    box-shadow: 0px 0px 99px $primary-color;
    border-radius: 21px;
    position: relative;
    display: flex;
    justify-content: center;

    @include lg {
        padding: 55px 135px;
    }
}
</style>