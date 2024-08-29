<script>
export default {
  name: 'formBinding',
  data() {
    return {
      colorFondo: '',
      colorTexto: '',
      mostrar: '',
      borde: '',
      contenido: '',
      opaco: '',
      tipoLetraSelected: '',
      tipoLetra: ['Franklin Gothic Medium', 'Times New Roman', 'Arial', 'sans-serif'],
      tamanoLetraSelected: '1rem',
      tamanoLetra: [
        { value: '1rem', label: 'Pequeño' },
        { value: '2rem', label: 'Mediano' },
        { value: '3rem', label: 'Grande' }
      ]
    }
  }
}
</script>
<template>
  <div class="container py-5">
    <h1 class="text-center mb-4">Personaliza la Figura</h1>
    <div class="row">
      <!--Izquierda (Formulario) -->
      <div class="col-md-5 mb-4">
        <form class="p-4 bg-light rounded shadow">
          <!-- Color de fondo -->
          <div class="mb-3">
            <label for="fondo" class="form-label">Color de fondo</label>
            <input type="color" id="fondo" v-model="colorFondo" class="form-control form-control-color" />
          </div>

          <!-- Color de texto -->
          <div class="mb-3">
            <label for="colorTexto" class="form-label">Color de texto</label>
            <input type="color" id="colorTexto" v-model="colorTexto" class="form-control form-control-color" />
          </div>

          <!-- Mostrar texto -->
          <div class="form-check form-switch mb-3">
            <input class="form-check-input" type="checkbox" id="mostrarTexto" v-model="mostrar" />
            <label class="form-check-label" for="mostrarTexto">Mostrar texto</label>
          </div>

          <!-- Borde -->
          <div class="mb-3">
            <label for="borde" class="form-label">Borde</label>
            <input type="range" id="borde" v-model="borde" min="0" max="50" class="form-range" />
          </div>

          <!-- Contenido -->
          <div class="mb-3">
            <label for="contenido" class="form-label">Contenido</label>
            <textarea id="contenido" v-model="contenido" rows="3" class="form-control"></textarea>
          </div>

          <!-- Tipografía -->
          <div class="mb-3">
            <label for="tipografia" class="form-label">Tipografía</label>
            <select id="tipografia" v-model="tipoLetraSelected" class="form-select">
              <option v-for="tipografia in tipoLetra" :key="tipografia" :value="tipografia">
                {{ tipografia }}
              </option>
            </select>
          </div>

          <!-- Opaco -->
          <div class="form-check form-switch mb-3">
            <input class="form-check-input" type="checkbox" id="opaco" v-model="opaco" />
            <label class="form-check-label" for="opaco">Opaco</label>
          </div>

          <!-- Tamaño de letra -->
          <div class="mb-3">
            <label class="form-label">Tamaño de letra</label>
            <div class="d-flex justify-content-between">
              <div v-for="tamano in tamanoLetra" :key="tamano.value" class="form-check">
                <input class="form-check-input" type="radio" :id="tamano.value" :value="tamano.value"
                  v-model="tamanoLetraSelected" />
                <label class="form-check-label" :for="tamano.value">{{ tamano.label }}</label>
              </div>
            </div>
          </div>
        </form>
      </div>

      <!--  Vista Previa de la figura  -->
      <div class="col-md-7 d-flex justify-content-center align-items-center">
        <div id="resultado"
          class="text-center d-flex justify-content-center align-items-center p-4 bg-white rounded shadow" :style="{
            backgroundColor: colorFondo + ' !important',
            color: colorTexto,
            borderRadius: `${borde}% !important`,
            fontFamily: tipoLetraSelected,
            fontSize: tamanoLetraSelected
          }" :class="{ 'opacity-50': opaco }">
          <p v-if="mostrar">{{ contenido || 'Escribe tu Contenido' }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
#resultado {
  width: 100%;
  max-width: 450px;
  height: 450px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

}
</style>
