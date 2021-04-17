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
export default {
  setup () {
    function onSubmit () {
      alert('Submitted')
    }

    return {
      onSubmit
    }
  }
}
</script>
