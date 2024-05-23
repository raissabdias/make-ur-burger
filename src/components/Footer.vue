<template>
    <footer id="footer">
        <p>Make Ur Burger &copy; {{ year }}.</p>
    </footer>
</template>

<script>
export default {
    name: "Footer",
    data() {
        return {
            year: new Date().getFullYear()
        }
    }
}
</script>

<style scoped>
    #footer {
        background: #222;
        height: 100px;
        color: #e3a00e;
        font-weight: 500;
        letter-spacing: 2px;
        display: flex;
        justify-content: center;
        align-items: center;
        bottom: 0;
    }
</style>