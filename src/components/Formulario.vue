<template>
  <div class="formulario">
    <h2 class="title">Detalles del Servicio</h2>
    <div class="image-container">
      <img :src="imagen24" alt="Imagen 24" class="img-pf" />
      <img :src="hadware" alt="Imagen de hardware" class="img-pf" />
      <ul class="h3-list">
        <li>Recepción en oficina</li>
        <li>Recojo de equipo</li>
        <li>Atención Programada</li>
        <li>Atención en línea</li>
        <li>Emergencia</li>
        <li>Atención las 24hrs</li>
      </ul>
    </div>

    <form @submit.prevent="enviarFormulario" class="formulario" id="formulario">
      <!-- Grupo: Nombre -->
      <div class="formulario__grupo" id="grupo__nombre">
        <label for="nombre" class="formulario__label">Contacto Recepción</label>
        <div class="formulario__grupo-input">
          <input type="text" class="formulario__input" name="nombre" id="nombre" placeholder="John Doe" v-model="nombre" required />
          <i class="formulario__validacion-estado fas fa-times-circle"></i>
        </div>
      </div>

      <!-- Grupo: Celular -->
      <div class="formulario__grupo" id="grupo__tel">
        <label for="tel" class="formulario__label">Celular</label>
        <div class="formulario__grupo-input">
          <input type="tel" class="formulario__input" name="tel" id="tel" placeholder="987654321" v-model="tel" required />
          <i class="formulario__validacion-estado fas fa-times-circle"></i>
        </div>
      </div>

      <!-- Grupo: Dirección -->
      <div class="formulario__grupo" id="grupo__direccion">
        <label for="direccion" class="formulario__label">Dirección</label>
        <div class="formulario__grupo-input">
          <input type="text" class="formulario__input" name="direccion" id="direccion" placeholder="Distrito X - Manzana X - Numero X" v-model="direccion" required />
          <i class="formulario__validacion-estado fas fa-times-circle"></i>
        </div>
      </div>

      <!-- Grupo: Correo Electrónico -->
      <div class="formulario__grupo" id="grupo__correo">
        <label for="correo" class="formulario__label">Correo Electrónico</label>
        <div class="formulario__grupo-input">
          <input type="email" class="formulario__input" name="correo" id="correo" placeholder="correo@correo.com" v-model="correo" required />
          <i class="formulario__validacion-estado fas fa-times-circle"></i>
        </div>
        <p class="formulario__input-error">El correo solo puede contener letras, números, puntos, guiones y guion bajo.</p>
      </div>

      <!-- Grupo: Hora de atención -->
      <div class="formulario__grupo" id="grupo__fecha-hora">
        <label for="fecha-hora" class="formulario__label">Hora de atención</label>
        <div class="formulario__grupo-input">
          <input type="text" class="formulario__input" name="fecha-hora" id="fecha-hora" placeholder="DD/MM/YYYY HH:MM:SS" v-model="fechaHora" readonly />
          <i class="formulario__validacion-estado fas fa-calendar-clock"></i>
        </div>
      </div>

      <!-- Grupo: Técnico Asignado -->
      <div class="formulario__grupo" id="grupo__tecnico">
        <label for="tecnico" class="formulario__label">Técnico Asignado</label>
        <div class="formulario__grupo-input">
          <select class="formulario__input" name="tecnico" id="tecnico" v-model="tecnico">
            <option value="" disabled selected>Seleccione un técnico</option>
            <option value="tecnico1">Técnico 1</option>
            <option value="tecnico2">Técnico 2</option>
            <option value="tecnico3">Técnico 3</option>
            <option value="tecnico4">Técnico 4</option>
          </select>
          <i class="formulario__validacion-estado fas fa-user-cog"></i>
        </div>
      </div>

      <!-- Sección de Satisfacción del Cliente -->
      <div class="formulario__grupo" id="grupo__satisfaccion">
        <label class="formulario__label">Satisfacción del Cliente/Solicitante</label>
        <div class="estrellas">
          <input type="radio" name="satisfaccion" id="estrella5" value="5"><label for="estrella5" title="5 estrellas">&#9733;</label>
          <input type="radio" name="satisfaccion" id="estrella4" value="4"><label for="estrella4" title="4 estrellas">&#9733;</label>
          <input type="radio" name="satisfaccion" id="estrella3" value="3"><label for="estrella3" title="3 estrellas">&#9733;</label>
          <input type="radio" name="satisfaccion" id="estrella2" value="2"><label for="estrella2" title="2 estrellas">&#9733;</label>
          <input type="radio" name="satisfaccion" id="estrella1" value="1"><label for="estrella1" title="1 estrella">&#9733;</label>
        </div>
      </div>

      <!-- Grupo: Estado del Servicio -->
      <div class="formulario__grupo" id="grupo__checkboxes">
        <label class="formulario__label">Estado del Servicio</label>
        <div class="checkboxes">
          <label><input type="checkbox" name="estado-servicio" value="concluido"> Concluido</label>
          <label><input type="checkbox" name="estado-servicio" value="diagnostico"> Diagnóstico</label>
          <label><input type="checkbox" name="estado-servicio" value="no-concluido"> No Concluido</label>
          <label><input type="checkbox" name="estado-servicio" value="traslado-tienda"> Traslado a Tienda</label>
          <label><input type="checkbox" name="estado-servicio" value="no-se-entra-personal"> No se Entra Personal</label>
          <label><input type="checkbox" name="estado-servicio" value="otros"> Otros</label>
        </div>
      </div>

      <div class="selector-botones">
        <button class="boton activo" id="boleta" @click.prevent="seleccionarBoton('boleta')">Boleta</button>
        <button class="boton" id="factura" @click.prevent="seleccionarBoton('factura')">Factura</button>
      </div>

      <div class="formulario__grupo formulario__grupo-btn-enviar">
        <button type="submit" class="formulario__btn">Enviar</button>
        <p class="formulario__mensaje-exito" id="formulario__mensaje-exito">Formulario enviado exitosamente!</p>
      </div>
    </form>
  </div>
</template>
