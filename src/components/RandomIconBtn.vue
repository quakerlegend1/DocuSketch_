<script setup>
import { ref } from 'vue';
import { fas } from '@fortawesome/free-solid-svg-icons'; // импортируем объект со всеми иконками solid
import { far } from '@fortawesome/free-regular-svg-icons'; // импортируем объект со всеми иконками regular

const solidArray = Object.values(fas).map(icon => icon.iconName)
const regularArray = Object.values(far).map(icon => icon.iconName)

let icon_solid = ref("user");
let icon_regular = ref("house");

const showRandomIcon = () => {
    setTimeout(() => {
        icon_solid.value = solidArray[Math.floor(Math.random() * solidArray.length)]
        icon_regular.value = regularArray[Math.floor(Math.random() * regularArray.length)]
    }, 3000)
}
</script>

<template>
    <div class="container">
        <button @click="showRandomIcon">
            Generate new icons
        </button>
        <div class="icn">
            <font-awesome-icon :icon="icon_solid" size="lg" />
            <font-awesome-icon :icon="icon_regular" size="lg" />
        </div>
    </div>
</template>

<style scoped>
.container {
    padding: 10px;
    border: 1px dotted red;
    width: fit-content;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.icn {
    border-radius: 10px;
    margin: 10px auto 0 auto;
    column-gap: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 90%;
    height: 50px;
    background-color: #bad362b0;
}
</style>