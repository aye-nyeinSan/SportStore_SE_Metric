<script setup>
import { ref } from 'vue'
import { useField, useForm } from 'vee-validate'

const { handleSubmit, handleReset } = useForm({
  validationSchema: {
    name(value) {
      if (value?.length >= 2) return true
      return 'Name needs to be at least 2 characters.'
    },
    phone(value) {
      if (/^[0-9-]{7,}$/.test(value)) return true
      return 'Phone number needs to be at least 7 digits.'
    },
    email(value) {
      if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true
      return 'Must be a valid e-mail.'
    },
    select(value) {
      if (value) return true
      return 'Select an item.'
    },
    checkbox(value) {
      if (value === '1') return true
      return 'Must be checked.'
    },
  },
})
const name = useField('name')
const phone = useField('phone')
const email = useField('email')
const select = useField('select')
const checkbox = useField('checkbox')

const items = ref([
  'Item 1',
  'Item 2',
  'Item 3',
  'Item 4',
])

const submit = handleSubmit(values => {
  alert(JSON.stringify(values, null, 2))
})
</script>

<template>
  <v-container class="form-container">
    <div class="form-wrapper">
      <h2 class="form-title">Log In</h2>
      <form @submit.prevent="submit" class="form-content">
        <v-text-field
          v-model="email.value.value"
          :error-messages="email.errorMessage.value"
          label="Email"
          class="form-input"
        ></v-text-field>

        <v-text-field
          v-model="email.value.value"
          :error-messages="email.errorMessage.value"
          label="Password"
          class="form-input"
        ></v-text-field>
        
        <div class="text-sm">
            <a href="#" class="font-semibold text-indigo-600 hover:text-indigo-500">
                Forgot password?
            </a>
        </div>
        <v-btn type="submit" class="form-button">LOG IN</v-btn>
      </form>
          <p class="mt-8 text-center"> Not a member yet? 
            <a href="#" class="font-semibold text-indigo-600 hover:text-indigo-500">Register Now</a>
          </p>
    
    </div>
  
             
  </v-container>
</template>

<style scoped>
.form-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.form-wrapper {
  background-color: white;
  border: 2px solid lightgray;
  border-radius: 10px;
  padding: 30px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  max-width: 500px;
  width: 100%;
}

.form-title {
  text-align: center;
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}

.form-content {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.form-input {
  background-color: #f8f8f8;
  border-radius: 5px;
}

.form-checkbox {
  display: flex;
  align-items: center;
}

.form-button {
  width: 100%;
  background-color: black;
  color: white;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}
</style>
