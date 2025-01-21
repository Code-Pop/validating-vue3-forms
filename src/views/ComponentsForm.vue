<template>
  <div>
    <h1>Create an Event</h1>
    <form @submit.prevent="createEvent">
      <BaseSelect
        v-model="event.category"
        label="Select a category"
        :options="categories"
        error="This field is required"
      />

      <h3>Name & describe your event</h3>
      <BaseInput
        v-model="event.title"
        label="Title"
        type="text"
        error="This field is required"
      />

      <BaseInput
        v-model="event.description"
        label="Description"
        type="text"
      />

      <h3>Where is your event?</h3>
      <BaseInput
        v-model="event.location"
        label="Location"
        type="text"
      />

      <h3>Are pets allowed?</h3>
      <BaseRadioGroup
        v-model="event.pets"
        name="pets"
        :options="[
          { value: 1, label: 'Yes' },
          { value: 0, label: 'No' }
        ]"
      />

      <template v-if="event.pets === 0">
        <h3>Are you sure? 🐶</h3>
        <BaseRadioGroup
          v-model="event.petsagain"
          name="petsagain"
          :options="[
            { value: 1, label: 'Yes' },
            { value: 0, label: 'No' }
          ]"
        />
      </template>

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          v-model="event.extras.catering"
          label="Catering"
        />
      </div>

      <div>
        <BaseCheckbox
          v-model="event.extras.music"
          label="Live music"
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

    <pre>{{ event }}</pre>
  </div>
</template>

<script>
export default {
  data () {
    return {
      categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community'
      ],
      event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: 1,
        extras: {
          catering: false,
          music: false
        }
      }
    }
  },
  methods: {
    createEvent () {
      console.log('submit')
    }
  }
}
</script>
