<template>
    <div>
        <h1>I am vuelidate form com</h1>
        <form @submit.prevent="submitForm">
            <div>
            <label>Name</label> <br>
            <input type="text" v-model="name"> <br>
            <span v-if="!$v.name.required && $v.name.$dirty" class="error">Name is required!</span>
            <span v-if="!$v.name.alpha && $v.name.$dirty" class="error">Name is required!</span>
            </div>
            <div>
            <label>Email</label> <br>
            <input type="email" v-model="email"> <br>
            <span v-if="(!$v.email.required || !$v.email.email) && $v.email.$dirty" class="error">Valid email is required!</span>
            </div>
            <div>
            <label>Password</label> <br>
            <input type="password" v-model="password"> <br>
            <span v-if="!$v.password.required && $v.password.$dirty" class="error">Password is required!</span>
            <span v-if="(!$v.password.minLength || !$v.password.maxLength) && $v.password.$dirty" class="error">Password must be between 6 nad 12 characters</span>
            </div>
            <div>
            <label>Gender</label> <br>
            <select v-model="gender">
                <option value="male">Male</option>
                <option value="female">Female</option>
                <option value="other">Other</option>
            </select> <br>
            <span v-if="!$v.gender.required && $v.gender.$dirty" class="error">Gender  is required!</span>
            </div>
            <div>
            <input type="checkbox" v-model="acceptTerms">
            <label>Accept Terms</label>
            </div> <br>
            <span v-if="!$v.acceptTerms.required && $v.acceptTerms.$dirty" class="error">acceptTerms  is required!</span> <br>
            <input type="submit">
        </form>
    </div>
</template>

<script>
// 
import { required, minLength, maxLength, alpha, email } from 'vuelidate/lib/validators'

export default {
    data(){
        return{
            name: '',
            email: '',
            password: '',
            gender: '',
            acceptTerms: ''
        }
    },
    validations:{
        name:{
            required,
            alpha
        },
        email:{
            required,
            email
        },
        password:{
            required,
            maxLength: maxLength(12),
            minLength: minLength(6),
        },
        gender:{
            required,
        },
        acceptTerms:{
            required
        }
    },
    methods:{
        submitForm(){
            this.$v.$touch();
            
            if(!this.$v.$invalid){
                console.log(`Name: ${this.name}, Email: ${this.email}, Password: ${this.password}, Gender: ${this.gender}, AcceptTerms: ${this.acceptTerms}`)
            }
        }
    }
}
</script>

<style scoped>
.error{
    color: red;
}
</style>
