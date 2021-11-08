<template>
  <section class="src-componentes-http">
    <div class="jumbotron">
      <h2>Componente HTTP</h2>
      <hr />

      <button class="btn btn-success my-3 mr-3" @click="pedirDatosAlServidor()">
        Pedir Axios
      </button>

      <div v-if="datos.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Email</th>
            <th>Telefono</th>
          </tr>
          <tr v-for="(post, index) in datos" :key="index">
            <td>{{ post.nombre }}</td>
            <td>{{ post.email }}</td>
            <td>{{ post.telefono }}</td>
          </tr>
        </table>
        <h4 class="alert alert-primary">
          Se encontraron {{ datos.length }} registros
        </h4>
      </div>
      <h4 v-else-if="peticion" class="alert alert-danger">Cargando datos...</h4>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-componentes-http",
  props: [],
  mounted() {},
  data() {
    return {
      url: "https://61893787d0821900178d7880.mockapi.io/api/usuarios",
      datos: [],
      peticion: false,
    };
  },
  methods: {
    async pedirDatosAlServidor() {
      try {
        this.datos = []
        this.peticion = true
        let respuesta = await this.axios(this.url);
        let datos = respuesta.data;
        console.log("datos GET", datos);
        this.datos = datos;
      } catch (error) {
        console.error("Error en recepción de datos del servidor", error);
      }
    },
  },
  computed: {},
};
</script>

<style scoped lang="css">
.src-componentes-http {
}
.jumbotron {
  /* Permalink - use to edit and share this gradient: https://colorzilla.com/gradient-editor/#006e2e+18,006e2e+100 */
  background: #006e2e; /* Old browsers */
  background: -moz-linear-gradient(
    top,
    #006e2e 18%,
    #006e2e 100%
  ); /* FF3.6-15 */
  background: -webkit-linear-gradient(
    top,
    #006e2e 18%,
    #006e2e 100%
  ); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(
    to bottom,
    #006e2e 18%,
    #006e2e 100%
  ); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#006e2e', endColorstr='#006e2e',GradientType=0 ); /* IE6-9 */

  color: white;
}
</style>
