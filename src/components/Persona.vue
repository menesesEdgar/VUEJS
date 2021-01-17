<template>
    <div>
        <template v-if="persona">
            <h1 v-text="datosPersona.nombre"></h1>
            <h2 v-text="datosPersona.correoe"></h2>
            <img :src="datosPersona.foto" alt="">
        </template>
    </div>
</template>
<script>
import axios from 'axios';
export default {
     mounted(){
         axios.get('https://randomuser.me/api/')
         .then((result) => {
            // Crear propiedad en el modelo
            this.persona = result.data.results[0];
         }).catch((err) => {
             
         });
     },
     data (){
         return {
             persona: null,
         }
     },
     computed: {
         datosPersona(){
             return {
             nombre: `${this.persona.name.first} ${this.persona.name.last}`,
             foto: this.persona.picture.large,
             correoe: this.persona.email
             }
         }
     }
}
</script>
<style>

</style>