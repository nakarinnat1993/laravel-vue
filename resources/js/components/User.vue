<template>
    <div class="user">
        <!-- <h1>This is User.vue</h1> -->
        <div class="container">
            <h2 class="text-center">แสดงข้อมูล</h2>
            <a href="users/create" class="btn btn-primary">Create</a>
            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>#</th>
                        <th>Name</th>
                        <th>City</th>
                        <th>Edit</th>
                        <th>Delete</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="user in users" :key="user.id">
                        <td>{{ user.id }}</td>
                        <td>{{ user.name }}</td>
                        <td>{{ user.city }}</td>
                        <td><a :href="'/users/'+user.id+'/edit'" class="btn btn-warning">Edit</a></td>
                        <td><a href="" class="btn btn-danger">Delete</a></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: "User",
    mounted() {
        this.getUsers();
    },
    methods: {
        getUsers() {
            console.log("getUsers");
            axios.get("api/users").then(response => {
                console.log(response);
                this.users = response.data;
            });
        }
    },
    data() {
        return {
            users:[
                {id:0,name:'',city:''}
            ],
        }
    },
};
</script>

<style></style>
