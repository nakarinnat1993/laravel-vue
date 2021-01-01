<template>
    <div class="edit">
        <div class="container">
            <h2 class="text-center">แก้ไขข้อมูล</h2>

            <form v-on:submit.prevent="updateUser">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input
                        type="text"
                        class="form-control"
                        id="name"
                        placeholder="Enter name"
                        v-model="name"
                    />
                </div>
                <div class="form-group">
                    <label for="city">City</label>
                    <input
                        type="text"
                        class="form-control"
                        id="city"
                        placeholder="City"
                        v-model="city"
                    />
                </div>
                <button type="submit" class="btn btn-primary" >Submit</button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name:"Edit",
    props:['id'],
    data() {
        return {
            name:"",
            city:"",
        }
    },
    mounted() {
        axios.get('/api/users/'+this.id).then( response =>{
            console.log(response.data);
            let user = response.data;
            this.name = user.name;
            this.city = user.city;
        });
    },
    methods: {
        updateUser(){
            console.log(this.name + this.city);
            axios.put('/api/users/'+this.id,{
                name:this.name,
                city:this.city
            }).then( () => {
                alert("แก้ไขข้อมูล "+this.name+" สำเร็จ");
                window.location.href = '/users';
            })

        }
    },
};
</script>

<style></style>
