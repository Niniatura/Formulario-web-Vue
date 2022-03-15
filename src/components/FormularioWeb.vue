<template>
<v-app>
    <v-card class="register-form">
        <v-form
            ref="form"
            v-model="valid"
            lazy-validation
        >
            <v-text-field
            v-model="name"
            :counter="10"
            :rules="nameRules"
            label="Name"
            required
            ></v-text-field>

            <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
            ></v-text-field>

            <v-select
            v-model="select"
            :items="items"
            :rules="selectRules"
            label="Item"
            required
            ></v-select>

            <v-text-field 
              :type="showPassword ? 'text' : 'password'" 
              prepend-icon="mdi-lock" append-icon="mdi-eye-off"
              label="Password"
              @click:append="showPassword = !showPassword" 
              :rules="passwordRules"
            />
            <v-btn
            :disabled="!valid"
            color="success"
            class="mr-4"
            @click="validate"
            >
            Validate
            </v-btn>
        </v-form>
    </v-card>
</v-app>
</template>

<script>
  export default {
    name:'FormularioWeb',
    data: () => ({
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ],
      selectRules: [
        v => !!v || 'Item is required',
      ],
      showPassword: false,
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$/.test(v)) || 'Minimum eight characters, at least one letter and one number'
      ],
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      }
    },
  }
</script>

<style scoped>
.register-form{
  max-width: 75%;
  margin-left: 15% !important;
}
</style>
