<template>
<div>
    <form @submit.prevent="handleSubmit">
        <label>First Name :</label>
        <input type="text" v-model="first_name" required>
        <div v-if="firstNameError" class="error">{{ firstNameError }} </div>

        <label>Last Name :</label>
        <input type="text" v-model="last_name" required>
        <div v-if="lastNameError" class="error">{{ lastNameError }} </div>

        <label>Email :</label>
        <input type="email" v-model="email" required>
        <div v-if="emailError" class="error">{{ emailError }} </div>

        <div class="button">
            <button class="submit" type="submit">Sign up here</button>
        </div>
    </form>

    <p> First Name: {{ first_name }} </p>
    <p> Last Name: {{ last_name }} </p>
    <p> Email: {{ email }} </p>
    
    
</div>

</template>


<script>
export default{

    data() {
        return {
            first_name: '',
            last_name: '',
            email: '',
            firstNameError: '',
            lastNameError: '',
            emailError: ''
        }
    },
    methods: {
       
        handleSubmit() {
            //Validate email field length
            this.firstNameError = this.first_name.length > 6 ? 
            '' : 'First Name should be more than 6 characters long!';

            this.lastNameError = this.last_name.length > 6 ? 
            '' : 'Last Name should be more than 6 characters long!';

            this.emailError = this.email.length > 6 ? 
            '' : 'email should be more than 6 characters long!';

            if(!this.firstNameError && !this.lastNameError && !this.emailError) {
                console.log(this.email);
                console.log(this.first_name);
                console.log(this.last_name);
            }

        }
    }
    
}
</script>


<style scoped> 

form {
    max-width: 600px;
    margin: 30px auto;
    background: #fff;
    text-align: left;
    padding: 20px;
    border-radius: 10px;
}

label {
    color: #aaa;
    display:inline-block;
    margin: 25px 0 15px;
    text-transform: uppercase;
}

input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: bordre-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

input[type="checkbox"] {
    display: inline-block;
    width:16px;
    margin: 0 10px 0;
    position: relative;
    top: 2px;
}

.pill {
    display: inline-block;
    margin: 20px 10px 0 0 ;
    padding: 6px 12px;
    border-radius: 20px;
    font-size: 12px;
    cursor: pointer;
    background: #eee;
}

button {
    background: rgb(7, 24, 7);
    border: 0;
    padding: 10px 20px;
    color: white;
    border-radius: 20px;
}

.submit {
    text-align: center;
}

.error {
    color: #ff0000;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}
</style>
