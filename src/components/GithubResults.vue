<template>
    <div class="result-wrapper">
        <!-- <table>
            <thead>
                <th>Login</th>
                <th>Type</th>
                <th>Avatar URL</th>
            </thead>
            <tbody v-if="results.items">
                <tr v-for="user in results.items" :key="user.login">
                    <td>{{ user.login }}</td>
                    <td>{{ user.type }}</td>
                    <td>{{ user.avatar_url }}</td>
                </tr>
            </tbody>

            <tbody v-else>
                <tr>
                    <td colspan="3" style="text-align:center;">No data found</td>
                </tr>
            </tbody>
        </table> -->

        <vue-good-table
            :columns="columns"
            :rows="results.items"
            :pagination-options="pagination"
        />
    </div>
</template>

<script>
    import { VueGoodTable } from 'vue-good-table';
    import 'vue-good-table/dist/vue-good-table.css'

    export default {
        props: ['results'],
        components: {
            VueGoodTable,
        },
        data() {
            return {
                columns: [
                    {
                        label: 'Login',
                        field: 'login',
                    },
                    {
                        label: 'Type',
                        field: 'type',
                    },
                    {
                        label: 'Avatar URL',
                        field: 'avatar_url',
                        
                    },
                ],
                pagination: {
                    enabled: true,
                    mode: 'records',
                    perPage: 9,
                    position: 'bottom', 
                }
            }
        }
    }
</script>

<style>
table.vgt-table {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 60%;
  text-align: left;
  margin: 20px auto;
}

.vgt-wrap__footer {
    width: 60%;
    margin: 0px auto;
    padding: 0px;
}

table.vgt-table td, table.vgt-table th {
  border: 1px solid #ddd;
  padding: 8px;
}

table.vgt-table tr:nth-child(even){background-color: #f2f2f2;}

table.vgt-table tr:hover {background-color: #ddd;}

table.vgt-table th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background: #04AA6D;
  color: #FFF;
}

.loader {
  border: 16px solid #f3f3f3;
  border-radius: 50%;
  border-top: 16px solid #3498db;
  width: 120px;
  height: 120px;
  -webkit-animation: spin 2s linear infinite; /* Safari */
  animation: spin 2s linear infinite;
}

/* Safari */
@-webkit-keyframes spin {
  0% { -webkit-transform: rotate(0deg); }
  100% { -webkit-transform: rotate(360deg); }
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>