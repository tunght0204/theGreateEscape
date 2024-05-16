<template>
  <div class="registration-form">
    <div class="register-header-img">
      <img src="@/assets/main/logotge_cropped.png" />
    </div>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label>First Name:</label>
        <input
          id="firstNameInput"
          type="string"
          class="form-control"
          :class="{ 'is-invalid': validator.firstName }"
          v-model="formData.firstName"
        />
      </div>
      <div class="validation-error-message" :class="{ visible: validator.firstName }">
        Please provide your first name.
      </div>
      <div class="form-group">
        <label>Last Name:</label>
        <input
          id="lastNameInput"
          type="string"
          class="form-control"
          :class="{ 'is-invalid': validator.lastName }"
          v-model="formData.lastName"
        />
      </div>
      <div class="validation-error-message" :class="{ visible: validator.lastName }">
        Please provide your last name.
      </div>
      <div class="form-group">
        <label>Email:</label>
        <input
          id="emailInput"
          type="string"
          class="form-control"
          :class="{ 'is-invalid': validator.email }"
          v-model="formData.email"
        />
      </div>
      <div class="validation-error-message" :class="{ visible: validator.email }">
        Please provide your email.
      </div>
      <div class="form-group">
        <label>Password:</label>
        <input
          id="passWordInput"
          type="password"
          class="form-control"
          :class="{ 'is-invalid': validator.password }"
          v-model="formData.password"
        />
      </div>
      <div class="validation-error-message" :class="{ visible: validator.password }">
        Password must be 8 characters or more and contain uppercase, lowercase, digit, and special
        character.
      </div>
      <div class="form-group">
        <label>Confirm Password:</label>
        <input
          id="confirmPassword"
          type="password"
          class="form-control"
          :class="{ 'is-invalid': validator.confirmPassword }"
          v-model="formData.confirmPassword"
        />
      </div>
      <div class="validation-error-message" :class="{ visible: validator.confirmPassword }">
        Please confirm your password again.
      </div>

      <img src="@/assets/main/newRegisterBtn.png" class="button-img" v-on:click="submitForm" />
    </form>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
interface FormData {
  firstName: string
  lastName: string
  email: string
  password: string
  confirmPassword: string
}

const formData = ref<FormData>({
  firstName: '',
  lastName: '',
  email: '',
  password: '',
  confirmPassword: ''
})

interface Validator {
  firstName: boolean | null
  lastName: boolean | null
  email: boolean | null
  password: boolean | null
  confirmPassword: boolean | null
}

const validator = ref<Validator>({
  firstName: null,
  lastName: null,
  email: null,
  password: null,
  confirmPassword: null
})

const submitForm = () => {
  formValidator()
  console.log('Form submitted:', validator)
}

const formValidator = () => {
  validator.value.firstName = formData.value.firstName.trim() === '' ? true : false
  validator.value.lastName = formData.value.lastName.trim() === '' ? true : false
  validator.value.email = validateEmail(formData.value.email)
  validator.value.password = validatePassword(formData.value.password)
  validator.value.confirmPassword = formData.value.confirmPassword !== formData.value.password
}

const validateEmail = (email: string): boolean => {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  //return true on fail the validation
  return !emailRegex.test(email.trim())
}

const validatePassword = (password: string): boolean => {
  const minLength = 8
  const uppercaseRegex = /[A-Z]/
  const lowercaseRegex = /[a-z]/
  const digitRegex = /[0-9]/
  const specialCharRegex = /[^A-Za-z0-9]/

  return !(
    password.trim() !== '' &&
    password.length >= minLength &&
    uppercaseRegex.test(password) &&
    lowercaseRegex.test(password) &&
    digitRegex.test(password) &&
    specialCharRegex.test(password)
  )
}
</script>
<style scoped>
.registration-form {
  width: 450px;
  padding: 40px;
  background-image: url('@/assets/main/IMG-COLOR-BG.jpg');
  background-position: center center;
  border: 5px solid #df6631;
  border-radius: 20px;
}

.validation-error-message {
  visibility: hidden;
  width: fit-content;
  padding: 4px 20px;
  margin: 4px 0;
  font-size: 0.875em;
  background-color: #dc3545;
  color: white;
  border-radius: 5px;
}

.validation-error-message.visible {
  visibility: visible;
}

.form-group {
  display: flex;
  align-items: center;
  background-color: #a93b3a;
  color: #f8ca0c;
  border-radius: 20px;
  padding-left: 10px;

  label {
    min-width: 140px;
    font-weight: 500;
  }

  input {
    flex: 1;
    border-radius: 0 20px 20px 0;
  }
}

.register-header-img {
  position: absolute;
  top: -135px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1;
}

.button-img {
  cursor: pointer;
  transition: transform 0.3s ease;
}

.button-img:hover {
  transform: scale(1.05);
}
</style>
