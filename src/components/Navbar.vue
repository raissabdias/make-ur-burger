<template>
    <div id="nav">
        <RouterLink to="/" id="logo_url">
            <img :src="logo" :alt="alt" id="logo">
        </RouterLink>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/order">Orders</RouterLink>
    </div>
</template>

<script>
export default {
    name: "Navbar",
    props: ["logo", "alt"]
}
</script>

<style scoped>
    #nav {
        background: #222;
        border-bottom: 3px solid #000;
        padding: 10px 40px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    #nav #logo_url {
        margin: auto;
        margin-left: 0;
    }

    #logo {
        width: 40px;
        height: 40px;
    }

    #nav a {
        color: #e3a00e;
        font-weight: 600;
        text-decoration: none;
        transition: .5s;
        margin-left: 30px;
        text-shadow: 1px 1px 1px solid;
        font-size: 1.2em;
    }

    #nav a:hover {
        color: #FFF;
    }
</style>