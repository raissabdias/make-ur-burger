<template>
    <div>
        <table id="burger-table">
            <tr>
                <th>#</th>
                <th>Client</th>
                <th>Bread</th>
                <th>Meat</th>
                <th>Optionals</th>
                <th>Ações</th>
            </tr>
            <tr>
                <td>0001</td>
                <td>Raíssa Dias</td>
                <td>Bread</td>
                <td>Meat</td>
                <td>Optionals</td>
                <td>
                    <select name="status" class="status">
                        <option>Select the burger status</option>
                    </select>
                    <button class="btn-delete">Cancel</button>
                </td>
            </tr>
            <tr>
                <td>0001</td>
                <td>Raíssa Dias</td>
                <td>Bread</td>
                <td>Meat</td>
                <td>Optionals</td>
                <td>
                    <select name="status" class="status">
                        <option>Select the burger status</option>
                    </select>
                    <button class="btn-delete">Cancel</button>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name: "Dashboard"
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