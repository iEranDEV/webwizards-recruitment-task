<template>
    <div id="aboutSection">
        <div id="aboutWrapper">
            <div id="aboutImg"></div>
            <div id="aboutText">
                <h1>O MNIE</h1>
                <span id="aboutContent">
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
#aboutContent {
    letter-spacing: 0px;
    font-size: 16px;
    margin-top: 45px;
}

#aboutSection {
    background: $white-color;
    display: flex;
    align-items: center;
    min-height: 100lvh;
    padding-top: 100px;

    @include md {
        margin-top: 0px;
    }
}

#aboutImg {
    width: 100%;
    height: 600px;
    background-image: url("./about_img.png");
    background-position: bottom;
    background-repeat: no-repeat;

    @include md {
        grid-area: 1 / 1 / 2 / 6;
    }

    @include xl {
        height: 100%;
        grid-area: 1 / 1 / 2 / 9;
    }
}

#aboutWrapper {
    display: flex;
    flex-direction: column;
    padding: 20px 20px;

    @include md {
        padding: 0px 0px;
        margin-right: 35px;
        display: grid;
        grid-template-columns: repeat(12, 1fr);
    }

    @include xl {
        grid-template-columns: 140px repeat(12, 1fr);
        margin-right: 140px;
    }
}

#aboutText {
    display: flex;
    flex-direction: column;
    width: 100%;

    @include md {
        grid-area: 1 / 7 / 6 / 13;
    }

    @include xl {
        grid-area: 1 / 10 / 2 / 14;
    }
}
</style>