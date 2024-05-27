<template>
    <div>
        <Message :msg="msg" v-show="msg" />
        <table id="burger-table">
            <tr>
                <th>#</th>
                <th>Client</th>
                <th>Bread</th>
                <th>Meat</th>
                <th>Optionals</th>
                <th>Ações</th>
            </tr>
            <tr v-for="burger in burgers" :key="burger.id">
                <td>{{ burger.id }}</td>
                <td>{{ burger.name }}</td>
                <td>{{ burger.bread }}</td>
                <td>{{ burger.meat }}</td>
                <td> {{ burger.optionals.join(', ') }}</td>
                <td>
                    <select name="status" class="status" @change="updateStatus(burger.id, $event)">
                        <option v-for="stat in status" :key="stat.id" :value="stat.type" :selected="burger.status == stat.type">
                            {{ stat.type }}
                        </option>
                    </select>
                    <button class="btn-delete" @click="deleteBurger(burger.id)">Cancel</button>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
import Message from './Message.vue';

export default {
    name: "Dashboard",
    data() {
        return {
            burgers: null,
            burger_id: null,
            status: [],
            msg: null
        }
    },
    components: {
        Message
    },
    methods: {
        async getOrders() {
            const request = await fetch("http://localhost:3000/burgers");
            const burgers = await request.json();
            this.burgers = burgers;

            this.getStatus();
        },
        async getStatus() {
            const request = await fetch("http://localhost:3000/status");
            const status = await request.json();
            this.status = status;
        },
        async deleteBurger(id) {
            const request = await fetch(`http://localhost:3000/burgers/${id}`, {
                method: 'DELETE'
            });

            this.msg = `Order #${id} was deleted successfully!`;
            setTimeout(() => this.msg = "", 3000);

            this.getOrders();
        },
        async updateStatus(id, event) {
            const status = event.target.value;
            const update = JSON.stringify({status: status});

            const request = await fetch(`http://localhost:3000/burgers/${id}`, {
                method: 'PATCH',
                headers: {
                    'Content-type': 'application/json'
                },
                body: update
            });

            this.msg = `Order #${id} was updated successfully!`;
            setTimeout(() => this.msg = "", 3000);

            this.getOrders();
        }
    },
    mounted() {
        this.getOrders();
    }
}
</script>

<style scoped>
    #burger-table {
        width: 100%;
        border-spacing: 0;
    }

    #burger-table th {
        background: #e3a00e;
        border-bottom: 3px solid #c0860b;
        padding: 5px;
    }

    #burger-table th:last-child {
        max-width: 2600px;
        width: 260px;
    }

    #burger-table td {
        text-align: center;
        padding: 10px 3px;    
        border-bottom: 1px solid #000000;
    }

    select  {
        padding: 7px 10px;
        border: 1px solid #e3a00e;
        border-radius: 8px;
    }

    .btn-delete {
        background: rgb(158, 0, 0);
        border: 2px solid rgb(158, 0, 0);
        color: white;
        text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.396);
        border-radius: 8px;
        padding: 7px 10px;
        font-weight: 500;
        transition: .5s;
        cursor: pointer;
        margin-left: 5px;
    }

    .btn-delete:hover {
        background: white;
        color: rgb(158, 0, 0);
        text-shadow: unset;
    }
</style>