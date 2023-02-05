<template>
    <div>
        <div class="card mt-3">
            <div class="card-body">
                <h3>Manage Users</h3>
            </div>
            <table class="table table-hover">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Email</th>
                        <th>User Since</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody v-if="results !== null">
                    <tr v-for="user in results.data">
                        <td>{{ user.name }}</td>
                        <td>{{ user.email }}</td>
                        <td>{{ user.member_since }}</td>
                        <td>
                            <div class="btn-group">
                                <button class="btn btn-warning btn-sm"><i class="fas fa-edit"></i></button>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    mounted(){
        this.getUsers()
    },
    data() {
        return {
            results: null,
            params:{
                page: 1
            }
        }
    },
    methods: {
        getUsers: function () {
            axios.get('/data/users',{params: this.params}).then(response => {
                this.results = response.data.results
            })
        }
    }
}
</script>