<template>
  <form @submit.prevent="onSubmit">
    <BaseInput
      label="Email"
      type="email"
      v-model="email"
      :error="emailError"
    />

    <BaseInput
      label="Password"
      type="password"
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
import { useField } from 'vee-validate'
export default {
  setup () {
    function onSubmit () {
      alert('Submitted')
    }

    const { value: email, errorMessage: emailError } = useField('email', (value) {
      if (!value) return 'This field is required'

      const regex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      if (!regex.test(String(value).toLowerCase())) {
        return 'Please enter a valid email address'
      }

      return true
    })

    return {
      onSubmit,
      email,
      emailError
    }
  }
}
</script>
