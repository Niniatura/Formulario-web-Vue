<template>
  <div>
      <form action="" @submit.prevent="contacto">
          <label for="nombre">Nombre</label>
          <input 
            type="text"
            v-model="name"
            id="nombre"
            required
            placeholder="Ingresar nombre">

            <label for="email">Email</label>
            <input 
            type="email"
            v-model="email"
            id="email"
            required
            placeholder="Ingresar email">

            <label for="password">Password</label>
            <input 
            type="password"
            v-model="password"
            id="password"
            required
            placeholder="Ingresar password">

            <p v-if="editedPassword && !passwordHasNumbers">Error. La contraseña debe tener al menos un número</p>

            <input type="submit" value="Contactar">
      </form>
  </div>
</template>

<script>
export default {
    name:'FormularioWeb',
    data(){
        return{
            name:'',
            email:'',
            editedPassword: null
        }
    },
    computed: {
        passwordHasNumbers(){
            return /\d/.test(this.editedPassword);
        }
    }
}
</script>

<style>

</style>