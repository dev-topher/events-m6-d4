<template>
  <div id="app">
    <CitaFormulario @agregar-cita="agregarCita" />
    <div v-if="citas.length === 0" class="no-citas">
      <p>Aún no hay consultas registradas</p>
    </div>
    <div v-else class="tarjetas-container">
      <CitaCard
        v-for="(cita, index) in citas"
        :key="cita.fecha + cita.hora"
        :cita="cita"
        @eliminar-cita="eliminarCita(index)"
      />
    </div>
  </div>
</template>

<script>
import CitaFormulario from './components/CitaFormulario.vue';
import CitaCard from './components/CitaCard.vue';

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
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 60px;
}

.tarjetas-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
    width: 100%;
  }

.no-citas {
    font-size: 20px;
    text-align: center;
    color: #FF2800;
    margin-top: 20px;
  }
</style>