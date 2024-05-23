<template>
    <div id="main-banner">
        <div>
            <h1>Make Ur Burger</h1>
            <p>Customize your burger with your favorite ingredients.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Banner"
}
</script>

<style scoped>
    #main-banner {
        height: 70vh;
        background-image: url('img/background.png');
        background-size: cover;
        background-position: 0 -100px;
        display: flex;
        align-items: center;
        justify-content: left;
        text-shadow: 1px 1px 1px black;
        padding: 0 150px;
    }

    #main-banner h1 {
        color: #e3a00e;
        text-transform: uppercase;
    }

    #main-banner p {
        letter-spacing: 3px;
        color: white;
    }
</style>