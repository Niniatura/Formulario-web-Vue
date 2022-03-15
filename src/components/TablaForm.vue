<template>
    <table class="table">
        <thead>
            <tr>
            <th scope="col">Campo</th>
            <th scope="col">Dato Ingresado</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item) in datosTabla" :key="item">
                <td>{{datos.nombre}}</td>
                <td>{{datos.email}}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
    //import FormularioWeb from './FormularioWeb.vue'
    export default{
        name:'TablaForm',
        data: () => ({
           //datos
        }),
        props:['datosTabla']
    }
</script>

<style scoped>
.table{
    width: 50%;
    align-self: center;
}
.table-info{
    color: darkblue; 
}
</style>