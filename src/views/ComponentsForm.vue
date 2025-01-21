<template>
  <div>
    <h1>Create an Event</h1>
    <form>
      <BaseSelect
        v-model=""
        label="Select a category"
        :options="categories"
        :error=""
      />

      <h3>Name & describe your event</h3>
      <BaseInput
        v-model=""
        label="Title"
        :error=""
        type="text"
      />

      <BaseInput
        v-model=""
        label="Description"
        :error=""
        type="text"
      />

      <h3>Where is your event?</h3>
      <BaseInput
        v-model=""
        label="Location"
        :error=""
        type="text"
      />

      <h3>Are pets allowed?</h3>
      <BaseRadioGroup
        v-model=""
        :error=""
        name="pets"
        :options="[
          { value: 1, label: 'Yes' },
          { value: 0, label: 'No' }
        ]"
      />

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          v-model=""
          label="Catering"
          :error=""
        />
      </div>

      <div>
        <BaseCheckbox
          v-model=""
          label="Live music"
          :error=""
        />
      </div>

      <div>
        <BaseButton
          type="submit"
          class="-fill-gradient"
          something="else"
        >
          Submit
        </BaseButton>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  setup () {
    const required = value => {
      const requiredMessage = 'This field is required'
      if (value === undefined || value === null) return requiredMessage
      if (!String(value).length) return requiredMessage

      return true
    }

    const minLength = (number, value) => {
      if (String(value).length < number) return 'Please type at least ' + number + ' characters'

      return true
    }

    const anything = () => {
      return true
    }

    return {}
  }
}
</script>
