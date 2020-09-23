<template>
    <div class="button-box">
        <div>{{ text }}</div>
    </div>
</template>

<script>
export default {
    name: 'Button', 
    props: {
        text: String,
    },
}
</script>

<style scoped>

    .button-box {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin-top: 10px;
        margin-left: 5px;
        width: 65px;
        height: 65px;
        text-align: center;
        font-family: 'Roboto', sans-serif;
        font-size: 30px;

        border-radius: 100%;
        background-color: #2b2929;
    }

</style>