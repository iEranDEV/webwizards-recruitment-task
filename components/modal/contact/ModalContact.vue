<template>
    <ModalWrapper>
        <!-- Contact form -->
        <form id="contactForm" @submit="handleSubmit">
            <!-- Name input -->
            <div class="inputWrapper">
                <label for="name" class="inputLabel required"> IMIĘ </label>
                <input
                    v-model="name"
                    id="name"
                    name="name"
                    type="text"
                    class="input"
                    placeholder="- wpisz -"
                />
            </div>

            <!-- Last name input -->
            <div class="inputWrapper">
                <label for="surname" class="inputLabel required">
                    NAZWISKO
                </label>
                <input
                    v-model="surname"
                    id="surname"
                    name="surname"
                    type="text"
                    class="input"
                    placeholder="- wpisz -"
                />
            </div>

            <!-- Email input -->
            <div class="inputWrapper">
                <label for="email" class="inputLabel required">
                    ADRES E-MAIL
                </label>
                <input
                    v-model="email"
                    id="email"
                    name="email"
                    type="text"
                    class="input"
                    placeholder="- wpisz -"
                />
            </div>

            <!-- Requirement symbol -->
            <p id="formRequirement"><span>*</span> - pola wymagane</p>

            <!-- Accept input -->
            <div id="acceptWrapper">
                <input v-model="accept" type="checkbox" />
                <span>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.
                </span>
            </div>

            <!-- Confirm button -->
            <button type="submit">WYŚLIJ</button>

            <!-- Error text -->
            <p v-if="isError" class="errorText">
                Proszę uzupełnić wymagane pola!
            </p>
        </form>

        <!-- Modal close button -->
        <div @click="close" class="modalCloseButton">
            <X />
        </div>
    </ModalWrapper>
</template>

<script setup lang="ts">
import { X } from "lucide-vue-next";

const props = defineProps<{
    close: Function;
}>();

const name = ref("");
const surname = ref("");
const email = ref("");
const accept = ref(false);
const isError = ref(false);

const handleSubmit = (e: SubmitEvent) => {
    e.preventDefault();

    let validate = true;

    // Validate name & surname
    if (
        !name ||
        !surname ||
        name.value.length < 3 ||
        surname.value.length < 3
    ) {
        validate = false;
    }

    // Validate email
    if (
        !/^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\.[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$/.test(
            email.value
        )
    ) {
        validate = false;
    }

    // Validate accept
    if (!accept.value) {
        validate = false;
    }

    if (validate) {
        console.log({
            name: name.value,
            surname: surname.value,
            email: email.value,
            accept: accept.value,
        });
    } else {
        isError.value = true;
    }
};
</script>

<style lang="scss">
.modalCloseButton {
    color: $gray-color;
    position: absolute;
    right: 20px;
    top: 20px;
    cursor: pointer;
}

#contactForm {
    display: flex;
    flex-direction: column;
    gap: 15px;
    width: 260px;

    button[type="submit"] {
        all: unset;
        background-color: $primary-color;
        width: 100%;
        padding: 11px 0px;
        border-radius: 6px;
        color: $white-color;
        font-size: 16px;
        display: flex;
        justify-content: center;
        align-items: center;
        letter-spacing: 0px;
        cursor: pointer;
        transition: all 0.5s;

        &:hover {
            letter-spacing: 6.4px;
        }
    }
}

.inputWrapper {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 100%;
}

.inputLabel {
    color: $gray-color;
    font-size: 12px;
    letter-spacing: 4.8px;
    position: relative;
}

.required::after {
    content: "*";
    position: absolute;
    color: $primary-color;
}

.input {
    all: unset;
    border-radius: 6px;
    width: 100%;
    box-sizing: border-box;
    padding: 14px 16px;
    display: flex;
    align-items: center;
    border: 1px solid $gray-color;
}

.input::placeholder {
    color: $gray-color;
    font-size: 12px;
    letter-spacing: 4.8px;
}

.errorText {
    font-size: 12px;
    color: $primary-color;
    text-align: center;
}

#formRequirement {
    font-size: 12px;

    &::first-letter {
        color: $primary-color;
    }
}

#acceptWrapper {
    display: flex;
    align-items: flex-start;
    gap: 8px;

    span {
        width: 100%;
        font-size: 10px;
    }
}
</style>