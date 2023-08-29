<template>
    <div id="about_section">
        <div id="about_wrapper">
            <div id="about_me_img"></div>
            <div id="about_me_text">
                <h1>O MNIE</h1>
                <span style="margin-top: 45px">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.
                    <br /><br />
                    Duis aute irure dolor in reprehenderit in voluptate velit
                    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
                    occaecat cupidatat non proident, sunt in culpa qui officia
                    deserunt mollit anim id est laborum.
                    <br /><br />
                    Sed ut perspiciatis unde omnis iste natus error sit
                    voluptatem accusantium doloremque laudantium, totam rem
                    aperiam, eaque ipsa quae ab illo inventore veritatis et
                    quasi architecto beatae vitae dicta sunt explicabo. Nemo
                    enim ipsam voluptatem quia voluptas sit aspernatur aut odit
                    aut fugit, sed quia consequuntur magni dolores eos qui
                    ratione voluptatem sequi nesciunt.
                    <br /><br />
                    Neque porro quisquam est, qui dolorem ipsum quia dolor sit
                    amet, consectetur, adipisci velit, sed quia non numquam.
                </span>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
#about_section {
    background: $white-color;
    display: flex;
    align-items: center;
    height: auto;

    @include xl {
        height: 100lvh;
    }
}

#about_me_img {
    width: 100%;
    height: 600px;
    background-image: url("./about_img.png");
    background-position: bottom;
    background-repeat: no-repeat;

    @include lg {
        grid-area: 1 / 1 / 2 / 6;
    }

    @include xl {
        height: 100%;
        grid-area: 1 / 1 / 2 / 9;
    }
}

#about_wrapper {
    display: flex;
    flex-direction: column;
    padding: 20px 20px;

    @include lg {
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        column-gap: 16px;
    }

    @include xl {
        padding: 0px 0px;
        grid-template-columns: 140px repeat(12, 1fr);
        margin-right: 140px;
    }
}

#about_me_text {
    display: flex;
    flex-direction: column;
    width: 100%;

    @include lg {
        grid-area: 1 / 7 / 6 / 13;
    }

    @include xl {
        grid-area: 1 / 10 / 2 / 14;
    }
}
</style>