<template>
  <section id="CarAlquiler" class="w-80">
    <form v-show="showFormCar">
      <h1 class="mb-2">Complete el siguiente formulario:</h1>
      
      <div class="grid justify-items-center"> 
      <label class="mt-2 ">Nombre:</label>
      <input v-model="nombre" type="text" id="nombre" class="rounded w-48">
    </div> 
  <div class="grid justify-items-center"> 
      <label class="mt-2">Apellidos:</label>
      <input v-model="apellidos" type="text" id="apellidos" class="w-48" >
    </div> 
  <div class="grid justify-items-center"> 
      <label class="mt-2 w-64">Ciudad de recogida:</label>
      <input v-model="ciudad" type="text" id="ciudad" class="rounded w-48">
    </div> 
  <div class="grid justify-items-center mb-4"> 
      <label class="w-64  ">Días en alquiler:</label>
      <input v-model="dias" type="text" id="dias" class="rounded w-48">
    </div> 
         
      <button type="button" @click="final" class="w-32">Enviar</button>
    </form>
    <BaucherAlquiler v-show="showBaucher" :baucher="baucher"></BaucherAlquiler>
  </section>
</template>

<script>
  import BaucherAlquiler from './BaucherAlquiler.vue'

export default {
  name: 'CarAlquiler',
  components: {
    BaucherAlquiler,
  },
  data: () => ({
    nombre: "",
    apellidos: "",
    ciudad: "",
    dias: 0,
    baucher:"",
    showBaucher:false,
    showFormCar:true
  }),

  methods: {
    final() {                      //creo un objeto con informacion y lo envio con los props
      this.baucher = {
        'nombre':this.nombre,
        'apellidos':this.apellidos,
        'ciudad':this.ciudad,
        'dias':this.dias,
        'precio':this.precio
      }
      this.showFormCar = false,
      this.showBaucher = true
    }
  },

  computed: {

    precio() {
      if (this.dias < 7) {
        return  25 * this.dias;
      } else {
        return 21.42 * this.dias;
      }
    }
  }
 
}
</script>

<style>

</style>
