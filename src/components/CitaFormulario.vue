<template>
    <div class="form-container">
      <form @submit.prevent="agregarCita">
        <div class="form-row">
          <div class="form-group">
            <label :style="{ color: paciente ? 'black' : 'red' }">Paciente</label>
            <input type="text" v-model="paciente" @input="validarFormulario" />
          </div>
          <div class="form-group">
            <label :style="{ color: fecha ? 'black' : 'red' }">Fecha</label>
            <input type="date" v-model="fecha" @input="validarFormulario" />
          </div>
          <div class="form-group">
            <label :style="{ color: hora ? 'black' : 'red' }">Hora</label>
            <input type="time" v-model="hora" @input="validarFormulario" />
          </div>
          <div class="form-group">
            <label :style="{ color: gravedad ? 'black' : 'red' }">Gravedad</label>
            <select v-model="gravedad" @input="validarFormulario">
              <option value="">Seleccione</option>
              <option value="Baja">Baja</option>
              <option value="Media">Media</option>
              <option value="Alta">Alta</option>
            </select>
          </div>
          <div class="form-group">
            <label :style="{ color: motivo ? 'black' : 'red' }">Motivo</label>
            <input type="text" v-model="motivo" @input="validarFormulario" />
          </div>
        </div>
        <div class="form-group-full">
          <button type="submit" :disabled="!formularioValido">Agregar</button>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: '',
        formularioValido: false,
      };
    },
    methods: {
      validarFormulario() {
        this.formularioValido = this.paciente && this.fecha && this.hora && this.gravedad && this.motivo;
      },
      agregarCita() {
        const nuevaCita = {
          paciente: this.paciente,
          fecha: this.fecha,
          hora: this.hora,
          gravedad: this.gravedad,
          motivo: this.motivo,
        };
        this.$emit('agregar-cita', nuevaCita);
        this.limpiarFormulario();
      },
      limpiarFormulario() {
        this.paciente = '';
        this.fecha = '';
        this.hora = '';
        this.gravedad = '';
        this.motivo = '';
        this.formularioValido = false;
      },
    },
  };
  </script>
  
  <style>
  .form-container {
    border: 2px solid darkgray;
    border-radius: 8px;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    max-width: 1000px; /* Aumentado el max-width */
    margin: auto;
  }
  
  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%; /* Asegurar que el formulario ocupa todo el ancho del contenedor */
  }
  
  .form-row {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }
  
  .form-group {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10px;
  }
  
  .form-group label {
    margin-bottom: 5px;
  }
  
  .form-group input,
  .form-group select {
    width: 150px;
    padding: 5px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  
  .form-group-full {
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  
  button {
    padding: 10px 20px;
    border-radius: 4px;
    border: none;
    background-color: #007bff;
    color: white;
    cursor: pointer;
  }
  
  button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  </style>
  