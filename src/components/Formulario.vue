<template>
  <div class="form-container">
    <!-- Navbar con imagen -->
    <div class="navbar">
      <img src="https://cuscoinformatico.com/storage/iconos/cuscoinformatico-logo.png" alt="Cusco Informatico" />
    </div>
    
    <h2>Formulario de Reserva de Equipos</h2>
    
    <!-- Formulario -->
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="equipo">Equipo a Reservar</label>
        <input type="text" id="equipo" v-model="formData.equipo" placeholder="Nombre del equipo" required />
      </div>
      
      <div class="form-group">
        <label for="tipo">Tipo de Dispositivos</label>
        <select id="tipo" v-model="formData.tipo" @change="mostrarOpciones">
          <option value="" disabled>Seleccione el tipo de dispositivo</option>
          <option value="Laptops">Laptops</option>
          <option value="PCs">PCs</option>
          <option value="Impresoras">Impresoras</option>
          <option value="Tablets">Tablets</option>
          <option value="Consolas">Consolas</option>
          <option value="Otros">Otros</option>
        </select>
      </div>
      
      <div class="form-group">
        <label for="marca">Marca</label>
        <select id="marca" v-model="formData.marca">
          <option value="" disabled>Seleccione una marca</option>
          <option v-for="marca in marcasDisponibles" :key="marca" :value="marca">
            {{ marca }}
          </option>
        </select>
      </div>
      
      <div class="form-group">
        <label for="fecha">Fecha de Reserva</label>
        <input type="date" id="fecha" v-model="formData.fecha" required />
      </div>
      
      <div class="form-group">
        <label for="hora">Hora de Reserva</label>
        <input type="time" id="hora" v-model="formData.hora" required />
      </div>
      
      <div class="form-group">
        <label for="name">Nombre del Cliente</label>
        <input type="text" id="name" v-model="formData.nombre" required />
      </div>
      
      <div class="form-group">
        <label for="tel">Teléfono</label>
        <input type="tel" id="tel" v-model="formData.telefono" required />
      </div>
      
      <div class="form-group">
        <label for="comentarios">Comentarios</label>
        <textarea id="comentarios" v-model="formData.comentarios" placeholder="Detalles adicionales..." rows="4"></textarea>
      </div>
      
      <div class="form-group">
        <button type="submit">Hacer Reserva</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "FormularioReserva",
  data() {
    return {
      formData: {
        equipo: "",
        tipo: "",
        marca: "",
        fecha: "",
        hora: "",
        nombre: "",
        telefono: "",
        comentarios: ""
      },
      opcionesMarcas: {
        Laptops: ["HP", "Lenovo", "Dell", "Apple", "Asus"],
        PCs: ["HP", "Lenovo", "Dell", "Acer", "Asus"],
        Impresoras: ["HP", "Epson", "Canon", "Brother"],
        Tablets: ["Apple", "Samsung", "Lenovo"],
        Consolas: ["Sony", "Microsoft", "Nintendo"],
        Otros: []
      },
      marcasDisponibles: []
    };
  },
  methods: {
    mostrarOpciones() {
      this.marcasDisponibles = this.opcionesMarcas[this.formData.tipo] || [];
      this.marcasDisponibles.push("Otra"); // Agrega "Otra" como última opción
    },
    submitForm() {
      console.log("Datos del formulario:", this.formData);
      alert("Reserva realizada con éxito");
    }
  }
};
</script>

<style lang="scss" scoped>
@import "./FormularioReserva.module.scss";
</style>
