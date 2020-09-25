<template>
    <div class="main">
        <div class="result">{{ current || '0' }}</div>
        <div class="keypad">
            <Button @click="clear" text="C" class="side-operation" />
            <Button @click="sign" text="&#x00B1;" class="side-operation" />
            <Button @click="percent" text="%" class="side-operation" />
            <Button @click="divide" text="&#247;" class="main-operation"/>

            <Button @click="append('7')" text="7"/>
            <Button @click="append('8')" text="8"/>
            <Button @click="append('9')" text="9"/>
            <Button @click="times" text="&#215;" class="main-operation"/>

            <Button @click="append('4')" text="4"/>
            <Button @click="append('5')" text="5"/>
            <Button @click="append('6')" text="6"/>
            <Button @click="minus" text="-" class="main-operation" />

            <Button @click="append('1')" text="1"/>
            <Button @click="append('2')" text="2"/>
            <Button @click="append('3')" text="3"/>
            <Button @click="plus" text="+" class="main-operation" />

            <Button @click="append(`${Math.round(Math.PI * 100) / 100}`)" text="&#960;"/>
            <Button @click="append('0')" text="0"/>
            <Button @click="dot" text="."/>
            <Button @click="equals" text="=" class="main-operation" />
        </div>
    </div>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Calculator',
    components: {
        Button,
    },
    data() {
        return {
            previous: null,
            current: '',
            operator: null,
            operatorClicked: false
        };
    },
    methods: {

        clear () {
            this.current = '';
        },

        sign () {
            this.current = this.current.charAt(0) === '-' ? 
                this.current.slice(1) : `-${this.current}`;
        },

        percent () {
            this.current = `${parseFloat(this.current) / 100}`;
        },

        append (number) {
            if (this.operatorClicked) {
                this.current = '';
                this.operatorClicked = false;
            }
            if (this.checkLength()){
                this.current = `${this.current}${number}`;
            }
        },

        dot () {
            this.current = this.current.indexOf(".") === -1 ?
                `${this.current}.` : this.current;
        }, 

        setPrevious () {
            this.previous = this.current;
            this.operatorClicked = true;
        },

        divide () {
            this.operator = (a, b) => a / b;
            this.setPrevious();
        },

        times () {
            this.operator = (a, b) => a * b;
            this.setPrevious();
        },

        minus () {
            this.operator = (a, b) => a - b;
            this.setPrevious();
        },

        plus () {
            this.operator = (a, b) => a + b;
        },

        equals () {
            this.current = `${this.operator(
                parseFloat(this.previous),
                parseFloat(this.current)
            )}`;
            this.previous = null;
        }, 

        checkLength () {
            return this.current.length < 10;
        }
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
        color: rgb(253, 254, 254);
        background-color: rgb(255,165,0);
        transition: all .5s ease-out;
    }

    .main-operation:active {
        color: rgb(255,165,0);
        background-color: rgb(253, 254, 254);
    }

    .side-operation {
        color: #000000;
        background-color: rgb(166, 172, 175);
        transition: background-color .5s ease-out;
    }

    .side-operation:active {
        background-color: rgb(240, 240, 240);

    }

</style>