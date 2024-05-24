<template>
    <div class="message-container">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
export default {
    name: "Message",
    props: {
        msg: String
    }
}
</script>

<style scoped>
    .message-container {
        color: rgb(17, 17, 147);
        background: rgb(228, 228, 254);
        border: 2px solid rgb(158, 158, 237);
        max-width: 300px;
        margin: 30px auto;
        padding: 10px;
        text-align: center;
        border-radius: 8px;
    }

    p {
        padding: 0;
        margin: 0;
    }
</style>