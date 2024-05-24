<template>
    <div>
        <p>Message component</p>
        <div>
            <form id="burger-form" method="POST" @submit="createBurger">
                <div class="input-container">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" v-model="name" placeholder="Enter your name">
                </div>
                <div class="input-container">
                    <label for="bread">Bread</label>
                    <select name="bread" id="bread" v-model="bread">
                        <option value="0">Choose your bread</option>
                        <option v-for="bread in bread_data" :key="bread.id" :value="bread.type">{{ bread.type }}</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="meat">Meat</label>
                    <select name="meat" id="meat" v-model="meat">
                        <option value="0">Choose your meat</option>
                        <option v-for="meat in meat_data" :key="meat.id" :value="meat.type">{{ meat.type }}</option>
                    </select>
                </div>
                <div class="input-container" id="optionals-container">
                    <label for="optional">Select your optionals</label>
                    <div class="checkbox-container" v-for="optional in optionals_data" :key="optional.id">
                        <input type="checkbox" name="optional" :value="optional.type">
                        <span>{{ optional.type }}</span>
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
    name: "BurgerForm",
    data() {
        return {
            bread_data: null,
            meat_data: null,
            optionals_data: null,
            name: null,
            bread: 0,
            meat: 0,
            optionals: [],
            status: 'Request',
            message: null
        }
    },
    methods: {
        async getIngredients() {
            const request = await fetch("http://localhost:3000/ingredients");
            const ingredients = await request.json();

            this.bread_data = ingredients.bread;
            this.meat_data = ingredients.meat;
            this.optionals_data = ingredients.optional;
        },
        async createBurger(e) {
            e.preventDefault();

            const data = {
                name: this.name,
                bread: this.bread,
                meat: this.meat,
                optionals: Object.keys(this.optionals),
                status: 'Requested'
            };
            
            const data_json = JSON.stringify(data);

            const request = await fetch("http://localhost:3000/burgers", {
                method: "POST",
                headers: {"Content-Type": "application/json"},
                body: data_json
            });

            const response = await request.json();
        }
    },
    mounted() {
        this.getIngredients();
    }
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
        margin-bottom: 25px;
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