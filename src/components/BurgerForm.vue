<template>
    <div>
        <p>Message component</p>
        <div>
            <form id="burger-form">
                <div class="input-container">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" v-model="name" placeholder="Enter your name">
                </div>
                <div class="input-container">
                    <label for="bread">Bread</label>
                    <select name="bread" id="bread" v-model="bread">
                        <option selected>Choose your bread</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="meat">Meat</label>
                    <select name="meat" id="meat" v-model="meat">
                        <option selected>Choose your meat</option>
                    </select>
                </div>
                <div class="input-container" id="optionals-container">
                    <label for="optional">Select your optionals</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="optional" value="Select">
                        <span>Salame</span>
                    </div><div class="checkbox-container">
                        <input type="checkbox" name="optional" value="Select">
                        <span>Salame</span>
                    </div><div class="checkbox-container">
                        <input type="checkbox" name="optional" value="Select">
                        <span>Salame</span>
                    </div><div class="checkbox-container">
                        <input type="checkbox" name="optional" value="Select">
                        <span>Salame</span>
                    </div><div class="checkbox-container">
                        <input type="checkbox" name="optional" value="Select">
                        <span>Salame</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" class="btn-submit" value="Make my burger!">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: "BurgerForm"
}
</script>

<style scoped>
    #burger-form {
        max-width: 400px;
        margin: 0 auto;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    label {
        text-align: center;
        font-weight: 600;
        margin-bottom: 10px;
    }

    input,
    select  {
        padding: 10px 15px;
        border: 1px solid #e3a00e;
        border-radius: 8px;
    }

    #optionals-container {
        flex-direction: row;
        flex-wrap: wrap;
    }

    #optionals-container label {
        width: 100%;
        margin-bottom: 20px;
    }

    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container input,
    .checkbox-container span {
        width: auto;
    }

    .checkbox-container span {
        margin-left: 5px;
    }

    .btn-submit {
        background: #e3a00e;
        border: 3px solid #e3a00e;
        font-weight: 600;
        cursor: pointer;
        letter-spacing: 2px;
        font-size: 1.1em;
        transition: .5s;
        width: 70%;
        margin: 0 auto;
    }

    .btn-submit:hover {
        background: white;
    }
</style>