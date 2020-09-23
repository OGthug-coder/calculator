<template>
    <div class="main">
        <div class="result">1234</div>
        <div class="keypad">
            <Button text="AC" class="side-operation" />
            <Button text="&#x00B1;" class="side-operation" />
            <Button text="&#37;" class="side-operation" />
            <Button text="&#247;" class="main-operation"/>

            <Button text="7"/>
            <Button text="8"/>
            <Button text="9"/>
            <Button text="&#215;" class="main-operation"/>

            <Button text="4"/>
            <Button text="5"/>
            <Button text="6"/>
            <Button text="-" class="main-operation" />

            <Button text="1"/>
            <Button text="2"/>
            <Button text="3"/>
            <Button text="+" class="main-operation" />

            <Button text="&#960;"/>
            <Button text="0"/>
            <Button text=","/>
            <Button text="=" class="main-operation" />
        </div>
    </div>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Calculator',
    components: {
        Button,
    }
}
</script>

<style scoped>
    .main {
        margin: auto;
        width: 320px;
    }

    .result {
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        align-items: flex-end;
        margin-right: 5px;
        height: 80px;
        width: 315px;
        font-size: 50px;
        font-family: 'Roboto', sans-serif;
        text-align: end;
        color: #ffffff;
    }

    .keypad {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        width: 320px;
        color: #ffffff;
    }

    .main-operation {
        background-color: #ffa500;
    }

    .side-operation {
        background-color: #808080;
    }

</style>