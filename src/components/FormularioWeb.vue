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
              v-model="password"
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
            @click="submit"
            >
            Submit
            </v-btn>
        </v-form>
    </v-card>
    <table class="table">
        <thead>
            <tr>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
            <th scope="col">Item</th>
            <th scope="col">Password</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in datosIngresados" :key="item">
                <td>{{item.Name}}</td>
                <td>{{item.Email}}</td>
                <td>{{item.Items}}</td>
                <td>{{item.Password}}</td>
            </tr>
        </tbody>
    </table>
</v-app>

</template>

<script>
  export default {
    name:'FormularioWeb',
    data: () => ({
      valid: true,
      datosIngresados:[],
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
      submit () {
        if(this.$refs.form.validate()){
            const datos = {
                        Name: this.name,
                        Email: this.email,
                        Items: this.select,
                        Password: this.password}
        this.datosIngresados.push(datos)
        }
        }
    },
}

  
</script>

<style scoped>
.register-form{
  max-width: 75%;
  margin-left: 15% !important;
}
.table{
    width: 50%;
    align-self: center;
}
.table-info{
    color: darkblue; 
}
</style>
