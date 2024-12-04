<template>
    <div class="citas-container">
      <CitaFormulario @agregar-cita="agregarCita" />
      <CitaCard
          v-for="(cita, index) in citas"
          :key="index"
          :cita="cita"
          @eliminar-cita="eliminarCita(index)"
        />
    </div>
  </template>
  
  <script>
  import CitaFormulario from './CitaFormulario.vue';
  import CitaCard from './CitaCard.vue';
  
  export default {
    components: {
      CitaFormulario,
      CitaCard,
    },
    data() {
      return {
        citas: [],
      };
    },
    methods: {
      agregarCita(cita) {
        this.citas.push(cita);
      },
      eliminarCita(index) {
        this.citas.splice(index, 1);
      },
    },
  };
  </script>
  
  