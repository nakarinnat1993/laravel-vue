<template>
    <div class="create">
        <div class="container">
            <h2 class="text-center">บันทึกข้อมูล</h2>

            <form v-on:submit.prevent="addUser">
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
    name:"Create",
    data() {
        return {
            name:"",
            city:"",
        }
    },
    methods: {
        addUser(){
            console.log(this.name + this.city);
            axios.post('/api/users',{
                name:this.name,
                city:this.city
            }).then( () => {
                alert("เพิ่มข้อมูล "+this.name+" สำเร็จ");
                this.name = "";
                this.city = "";
                window.location.href = '/users';
            })

        }
    },
};
</script>

<style></style>
