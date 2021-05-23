<template>
  <form @submit.prevent="onSubmit">
    <BaseInput
      label="Email"
      type="email"
      :error="emailError"
      :modelValue="email"
      @change="handleChange"
    />

    <BaseInput
      label="Password"
      type="password"
      v-model="password"
      :error="passwordError"
    />

    <BaseButton
      type="submit"
      class="-fill-gradient"
    >
    Submit
    </BaseButton>
  </form>
</template>

<script>
import { useField, useForm } from 'vee-validate'
export default {
  setup () {
    function onSubmit () {
      alert('Submitted')
    }

    const validations = {
      email: value => {
        if (!value) return 'This field is required'

        const regex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        if (!regex.test(String(value).toLowerCase())) {
          return 'Please enter a valid email address'
        }

        return true
      },
      password: value => {
        const requiredMessage = 'This field is required'
        if (value === undefined || value === null) return requiredMessage
        if (!String(value).length) return requiredMessage

        return true
      }
    }

    useForm({
      validationSchema: validations
    })

    const { value: email, errorMessage: emailError, handleChange } = useField('email')
    const { value: password, errorMessage: passwordError } = useField('password')

    return {
      onSubmit,
      email,
      emailError,
      password,
      passwordError,
      handleChange
    }
  }
}
</script>
