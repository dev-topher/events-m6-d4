<template>
    <div class="card" :class="gravedadClase">
      <h3>{{ cita.paciente }}</h3>
      <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
      <p><strong>Hora:</strong> {{ cita.hora }}</p>
      <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
      <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
      <button @click="eliminarCita">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cita: Object,
    },
    computed: {
      gravedadClase() {
        return {
          'bg-verde': this.cita.gravedad === 'Baja',
          'bg-amarillo': this.cita.gravedad === 'Media',
          'bg-rojo': this.cita.gravedad === 'Alta',
        };
      },
    },
    methods: {
      eliminarCita() {
        this.$emit('eliminar-cita');
      },
    },
  };
  </script>
  
  <style>
  .card {
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 20px;
    width: 200px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 10px; /* Asegura que cada tarjeta tenga un margen */
  }
  
  .card h3 {
    margin-bottom: 10px;
  }
  
  .card p {
    margin: 5px 0;
  }
  
  .card button {
    margin-top: 10px;
    padding: 5px 10px;
    border: none;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
  }
  
  .card button:hover {
    background-color: #0056b3;
  }
  
  .bg-verde {
    background-color: #d4edda;
  }
  
  .bg-amarillo {
    background-color: #fff3cd;
  }
  
  .bg-rojo {
    background-color: #f8d7da;
  }
  </style>
  