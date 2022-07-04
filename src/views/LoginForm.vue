<template>
  <form @submit.prevent="onSubmit">
    <BaseInput
      label="Email"
      type="email"
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
