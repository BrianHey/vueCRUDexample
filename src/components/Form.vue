<template>
  <div class="col-4">
    <h1 v-show="operacion == 'add'">Registrar un nuevo jugador</h1>
    <h1 v-show="operacion == 'update'">Editar un jugador</h1>
    <hr />
    <div class="form-group">
      <label>Nombre:</label>
      <input class="form-control" v-model="jugador.name" />
    </div>

    <div class="form-group">
      <label>Equipo:</label>
      <select class="form-control" v-model="jugador.team">
        <option value="Peru">Peru</option>
        <option value="Argentina">Argentina</option>
        <option value="Chile">Chile</option>
        <option value="Venezuela">Venezuela</option>
        <option value="Mexico">Mexico</option>
      </select>
    </div>
    <div class="form-group">
      <label>Edad:</label>
      <input class="form-control" v-model="jugador.age" />
    </div>

    <div class="form-group">
      <label>Posición:</label>
      <select class="form-control" v-model="jugador.position">
        <option value="Defensa">Defensa</option>
        <option value="Arquero">Arquero</option>
        <option value="Medio campista">Medio campista </option
        ><option value="Delantero">Delantero</option>
      </select>
    </div>

    <div class="form-group">
      <label>Número:</label>
      <input class="form-control" type="number" v-model="jugador.number" />
    </div>

    <div class="form-group">
      <label>Nacionalidad:</label>
      <select class="form-control" v-model="jugador.nation">
        <option value="Peruano">Peruano</option>
        <option value="Argentino">Argentino</option>
        <option value="Chileno">Chileno</option>
        <option value="Venezolano">Venezolano</option>
        <option value="Mexicano">Mexicano</option>
      </select>
    </div>

    <div class="form-group">
      <label>Puntos:</label>
      <input class="form-control" type="number" v-model="jugador.points" />
    </div>
    <button v-show="operacion == 'add'" @click="toctoc" class="btn btn-primary">
      Agregar
    </button>
    <button
      @click="editPlayer"
      v-show="operacion == 'update'"
      class="btn btn-warning"
    >
      Editar
    </button>
  </div>
</template>

<script>
export default {
  props: ["operacion", "player"],

  methods: {
    toctoc() {
      const jugador = Object.assign({}, this.jugador);
      this.$emit("QuienEs", jugador);
    },

    editPlayer() {
      const jugador = Object.assign({}, this.jugador);
      this.$emit("editPlayer", jugador);
    },
  },

  computed: {
    jugador() {
      const jugador = {
        name: "",
        team: "",
        age: "",
        position: "",
        number: "",
        nation: "",
        points: "",
      };
      const player = this.player;
      return player ? player : jugador;
    },
  },
};
</script>
