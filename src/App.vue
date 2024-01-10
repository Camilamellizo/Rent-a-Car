<template>
  <div id="app" class="container">
    <div class="flex justify-center">
      <img src="https://cdn.pixabay.com/photo/2014/04/03/00/41/race-car-309123_960_720.png" alt="car logo " class="w-32 drop-shadow-xl  rounded-full border border-solid bg-white">
    </div>
    <form  v-show="!canDrive">
      <div class="brand-title mb-8">CAR FOR EVERY ONE</div>
        <div>
          <label class="mb-8 text-xl">Carnet de Conducir:</label>
          <div class=" grid grid-cols-2 mt-8 text-xl mb-8">
            <div class="col-span-1  " >
              <input type="radio" value="si" v-model="result">Si
            </div>
            <div class="col-span-1">
              <input type="radio" value="no"  v-model="result">No
            </div>
          </div>
          <div class="grid justify-items-center">
            <label>Edad</label>
            <input  v-model="edad" type="text" placeholder="Number" class="bg-gray-100 border border-solid rounded px-4 mb-8 w-28"/>
          </div>
        </div>
      </form>
      <div class="text-center font-mono mt-4" v-show="!canDrive && result && edad">
        <p>NO cumples los requisitos<br> para alquilar uno de nuestros coches</p>
      </div>
    <CarAlquiler v-show="canDrive"></CarAlquiler>
    
  </div>
</template>


<script>

import CarAlquiler from './components/CarAlquiler.vue'


export default {
  name: 'App',
  components: {
    CarAlquiler,
   
  },
  data:() => ({
    result:'',
    edad:"",
   
  }),
  methods: {
    
  },
  computed: {
    
    canDrive() {
      if(this.edad>=18 && this.result == 'si'){
        return true
      } 
      else{
        return false
      }       
    }
  }
}
</script>
<style>
/* todo esto hace parte del formulario hasta donde acaba el style */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;900&display=swap');
body {
  margin: 0;
  width: 100vw;
  height: 100vh;
  background: #ecf0f3;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
  place-items: center;
  overflow: hidden;
  font-family: poppins;
}

.container {
  position: relative;
  width: 900px;
  height: 550px;
  border-radius: 20px;
  padding: 40px;
  box-sizing: border-box;
  background: #ecf0f3;
  box-shadow: 14px 14px 20px #cbced1, -14px -14px 20px white;
}



.brand-title {
  margin-top: 10px;
  font-weight: 900;
  font-size: 1.8rem;
  color: #1DA1F2;
  letter-spacing: 1px;
}



label, input, button {
  
  width: 20%;
  padding: 0;
  border: none;
  height: 80%;
  
 
}

label {
  margin-bottom: 4px;
}

label:nth-of-type(2) {
  margin-top: 12px;
}




button {
  color: white;
  margin-top: 20px;
  background: #1DA1F2;
  height: 40px;
  border-radius: 20px;
  cursor: pointer;
  font-weight: 900;
  box-shadow: 6px 6px 6px #cbced1, -6px -6px 6px white;
  transition: 0.5s;
}

button:hover {
  box-shadow: none;
}

a {
  position: absolute;
  font-size: 8px;
  bottom: 4px;
  right: 4px;
  text-decoration: none;
  color: black;
  background: yellow;
  border-radius: 10px;
  padding: 2px;
}


</style>
