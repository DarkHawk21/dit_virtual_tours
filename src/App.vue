<template>
  <div id="app">
    <h1 class="title">DIT Virtual Tours</h1>

    <div class="main-container">
      <div class="card">
        <div class="card-header">
          <h3>Elementos en SIV FC</h3>
        </div>
        
        <div class="card-body">
          <b id="esiv-fc-1"></b>
          <b id="esiv-fc-2"></b>
          <b id="esiv-fc-3"></b>
          <b id="esiv-fc-4"></b>
          <b id="esiv-fc-5"></b>

          <v-tour name="esiv-fc" :steps="stepsESIVFC" :options="options"></v-tour>
        </div>

        <div class="card-footer">
          <button class="button" @click="initTour('esiv-fc')">Iniciar tour</button>
        </div>
      </div>

      <div class="card">
        <div class="card-header">
          <h3>Elementos en CC FC</h3>
        </div>

        <div class="card-body">
          <b id="ecc-fc-1"></b>
          <b id="ecc-fc-2"></b>
          <b id="ecc-fc-3"></b>
          <b id="ecc-fc-4"></b>
          <b id="ecc-fc-5"></b>
        
          <v-tour name="ecc-fc" :steps="stepsECCFC" :options="options"></v-tour>
        </div>

        <div class="card-footer">
          <button class="button" @click="initTour('ecc-fc')">Iniciar tour</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "App",
    data () {
      return {
        options: {
          labels: {
            buttonSkip: 'Omitir tour',
            buttonPrevious: 'Anterior',
            buttonNext: 'Siguiente',
            buttonStop: 'Finalizar tour'
          }
        },
      }
    },
    methods: {
      initTour(tourName) {
        this.$tours[tourName].start();
      },
    },
    computed: {
      stepsESIVFC() {
        return [
          {
            target: '#esiv-fc-1',
            header: {
              title: 'Módulo de viáticos',
            },
            content: `Bienvenido al <b>Módulo de Viáticos</b>, Andrés Flores.<br>A continuación conoceremos los elementos de la interfaz.`
          },
          {
            target: '#esiv-fc-2',
            header: {
              title: 'Módulo de viáticos',
            },
            content: `En este menú puedes hacer búsquedas de las solicitudes creadas o iniciar nuevas solicitudes de Anticipos, Reembolsos o Vuelos.`
          },
          {
            target: '#esiv-fc-3',
            header: {
              title: 'Módulo de viáticos',
            },
            content: `En el <b>tablero principal</b> encontrarás los listados de las acciones que puedes realizar de acuerdo a tu rol, así como sus respectivos contadores y descripciones.`,
          },
          {
            target: '#esiv-fc-4',
            header: {
              title: 'Módulo de viáticos',
            },
            content: `Este es tu <b>tablero personal</b>, en él encontrarás los listados de las acciones que puedes hacer de acuerdo a tus solicitudes realizadas.`,
          },
          {
            target: '#esiv-fc-5',
            header: {
              title: '¡Genial!',
            },
            content: `Hemos terminado el tour del <b>Módulo de Viáticos</b>.<br>Si necesitas hacer de nuevo el recorrido, presiona el botón y comenzaremos una vez más.`,
          }
        ];
      },
      stepsECCFC() {
        return [
          {
            target: '#ecc-fc-1',
            header: {
              title: 'Módulo de Caja Chica',
            },
            content: `Bienvenido al <b>Módulo de Caja Chica</b>, Andrés Flores.<br>A continuación conoceremos los elementos de la interfaz.`
          },
          {
            target: '#ecc-fc-2',
            header: {
              title: 'Módulo de Caja Chica',
            },
            content: `En este menú puedes hacer búsquedas detalladas, crear nuevas cajas chicas o comprobar tus asignaciones de Caja chica.`
          },
          {
            target: '#ecc-fc-3',
            header: {
              title: 'Módulo de Caja Chica',
            },
            content: `En el <b>tablero principal</b> encontrarás los listados de las acciones que puedes realizar de acuerdo a tu rol, así como sus respectivos contadores y descripciones.`,
          },
          {
            target: '#ecc-fc-4',
            header: {
              title: 'Módulo de Caja Chica',
            },
            content: `Este es tu <b>tablero personal</b>, en él encontrarás los listados de las acciones que puedes hacer de acuerdo a tus solicitudes realizadas.`,
          },
          {
            target: '#ecc-fc-5',
            header: {
              title: '¡Genial!',
            },
            content: `Hemos terminado el tour del <b>Módulo de Caja Chica</b>.<br>Si necesitas hacer de nuevo el recorrido, presiona el botón y comenzaremos una vez más.`,
          }
        ];
      }
    }
  };
</script>

<style lang="scss">
  @import './sass/app.scss';
</style>