<template>
  <div>
    <h1>Create an Event</h1>
    <form @submit.prevent="submit">
      <BaseSelect
        v-model="category"
        label="Select a category"
        :options="categories"
        :error="errors.category"
      />

      <h3>Name & describe your event</h3>
      <BaseInput
        v-model="title"
        label="Title"
        type="text"
        :error="errors.title"
      />

      <BaseInput
        v-model="description"
        label="Description"
        type="text"
        :error="errors.description"
      />

      <h3>Where is your event?</h3>
      <BaseInput
        v-model="location"
        label="Location"
        type="text"
        :error="errors.location"
      />

      <h3>Are pets allowed?</h3>
      <BaseRadioGroup
        v-model="pets"
        name="pets"
        :options="[
          { value: 1, label: 'Yes' },
          { value: 0, label: 'No' }
        ]"
        :error="errors.pets"
      />

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          v-model="catering"
          label="Catering"
          :error="errors.catering"
        />
      </div>

      <div>
        <BaseCheckbox
          v-model="music"
          label="Live music"
          :error="errors.music"
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
import { useField, useForm } from 'vee-validate'
import { object, string, number, boolean } from 'yup'

export default {
  setup () {
    const validationSchema = object({
      category: string().required(),
      title: string().required('A cool title is required').min(3),
      description: string().required(),
      location: string(),
      pets: number(),
      catering: boolean(),
      music: boolean()
    })

    const { handleSubmit, errors } = useForm({
      validationSchema,
      initialValues: {
        pets: 1,
        catering: false,
        music: false
      }
    })

    const { value: category } = useField('category')
    const { value: title } = useField('title')
    const { value: description } = useField('description')
    const { value: location } = useField('location')
    const { value: pets } = useField('pets')
    const { value: catering } = useField('catering')
    const { value: music } = useField('music')

    const submit = handleSubmit(values => {
      console.log('submit', values)
    })

    return {
      category,
      title,
      description,
      location,
      pets,
      catering,
      music,
      submit,
      errors
    }
  },
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
      ]
    }
  }
}
</script>
