<template>
  <div class="component-form row justify-content-center mt-6">
    <b-form class="col-12 col-xl-8" novalidate>
      <b-form-group
        id="groupName"
        label="Name:"
        label-for="name">
        <b-form-input
          id="name"
          type="text"
          v-model.trim="name"
          required
          placeholder="Enter your name"
          :state="$v.name.$dirty && $v.name.$error ? false : null"
          @change="$v.name.$touch()" />
        <b-form-invalid-feedback v-if="!$v.name.required">Please enter your name.</b-form-invalid-feedback>
        <b-form-invalid-feedback v-if="!$v.name.minLength">Name must have at least {{$v.name.$params.minLength.min}} letters.</b-form-invalid-feedback>
      </b-form-group>
      <b-form-group
        id="groupEmail"
        label="Email:"
        label-for="email">
        <b-form-input
          id="email"
          type="email"
          v-model="email"
          required
          placeholder="Enter your email address"
          :state="$v.email.$dirty && $v.email.$error ? false : null"
          @change="$v.email.$touch()" />
        <b-form-invalid-feedback v-if="!$v.email.required">Please enter your email.</b-form-invalid-feedback>
        <b-form-invalid-feedback v-if="!$v.email.email">Please enter valid email.</b-form-invalid-feedback>
      </b-form-group>
      <b-form-group
        id="groupPhone"
        label="Phone:"
        label-for="phone">
        <masked-input
          type="text"
          name="phone"
          class="form-control"
          v-model="phone"
          :mask="['+', '1', ' ', '(', /[1-9]/, /\d/, /\d/, ')', ' ', /\d/, /\d/, /\d/, '-', /\d/, /\d/, /\d/, /\d/]"
          :guide="false"
          placeholderChar="#"
          required
          placeholder="Enter your phone number"
          :class="$v.phone.$dirty && $v.phone.$error ? 'is-invalid' : null"
          @blur="$v.phone.$touch()" />
        <b-form-invalid-feedback v-if="!$v.phone.required">Please enter your phone.</b-form-invalid-feedback>
        <b-form-invalid-feedback v-if="!$v.phone.minLength">Please enter valid phone.</b-form-invalid-feedback>
      </b-form-group>
      <b-form-group
        id="groupDescription"
        label="Description:"
        label-for="description">
        <b-form-textarea
          id="description"
          type="text"
          v-model="description"
          rows="3"
          max-rows="6"
          placeholder="Enter some description (max 100 words)"
          :state="countWords > 100 ? false : null" />
        <b-form-invalid-feedback v-if="countWords > 100">Description is limited to 100 words max. You've typed {{ countWords }}.</b-form-invalid-feedback>
      </b-form-group>
      <b-button
        type="submit"
        variant="primary"
        :disabled="$v.$invalid || countWords > 100"
        @click.prevent="onSubmit">Submit</b-button>
    </b-form>
    <b-modal ref="modalSuccess" hide-header hide-footer centered>
      <p class="h4">You've sent:</p>
      <hr>
      <p class="lead">
        Name: {{ name }}<br>
        Email: {{ email }}<br>
        Phone: {{ phone }}<br>
        <span v-if="description">Description: {{ description }}</span></p>
    </b-modal>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, minLength, email } from 'vuelidate/lib/validators'
import MaskedInput from 'vue-text-mask'

export default {
  name: 'Form',
  data() {
    return {
      isValidated: false,
      name: '',
      email: '',
      phone: '',
      description: ''
    }
  },
  components: {
    MaskedInput
  },
  mixins: [validationMixin],
  validations: {
    name: {
      required,
      minLength: minLength(3)
    },
    email: {
      required,
      email
    },
    phone: {
      required,
      minLength: minLength(17)
    }
  },
  computed: {
    countWords() {
      if (this.description) {
        return this.description.trim().split(/\s+/).length
      } else {
        return 0
      }
    }
  },
  methods: {
    onSubmit() {
      this.isValidated = true
      this.$refs.modalSuccess.show()
    }
  }
}
</script>
