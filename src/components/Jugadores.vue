<template>
  <div>
    <div class="row p-5 mx-0">
      <div class="col-4">
        <Form @QuienEs="addPlayer" operacion="add" />
      </div>

      <div class="col-8">
        <table class="table">
          <thead>
            <tr>
              <th>Nombre</th>
              <th>Equipo</th>
              <th>Edad</th>
              <th>Posición</th>
              <th>Número</th>
              <th>Nacionalidad</th>
              <th>Puntos</th>
              <th>acciones</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(j, i) in jugadores" :key="i">
              <td>{{ j.name }}</td>
              <td>{{ j.team }}</td>
              <td>{{ j.age }}</td>
              <td>{{ j.position }}</td>
              <td>{{ j.number }}</td>
              <td>{{ j.nation }}</td>
              <td>{{ j.points }}</td>
              <td>
                <button
                  data-toggle="modal"
                  data-target="#exampleModal"
                  class="btn btn-warning"
                  @click="editFields(i)"
                >
                  Editar
                </button>
                <button class="btn btn-danger" @click="deletePlayer(i)">
                  eliminar
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <div
      class="modal fade"
      id="exampleModal"
      tabindex="-1"
      role="dialog"
      aria-hidden="true"
    >
      <b-modal
        hide-header="true"
        hide-footer="true"
        v-model="show"
        id="modal-1"
        title="BootstrapVue"
      >
        <div class="col-12">
          <Form
            @editPlayer="editPlayer"
            operacion="update"
            :player="jugadorEdit"
          />
        </div>
      </b-modal>
    </div>
  </div>
</template>

<script>
import Form from "@/components/Form.vue";

export default {
  name: "Jugadores",
  data() {
    return {
      jugadores: [],
      jugadorEdit: {},
      playerIndex: null,
      show: false,
    };
  },
  components: {
    Form,
  },
  methods: {
    addPlayer(jugador) {
      this.jugadores.push(jugador);
    },

    deletePlayer(i) {
      console.log(this);
      this.jugadores.splice(i, 1);
    },

    editFields(i) {
      this.show = true;
      this.playerIndex = i;
      const jugador = Object.assign({}, this.jugadores[i]);
      this.jugadorEdit = jugador;
    },

    editPlayer(jugador) {
      const index = this.playerIndex;
      console.log(index);
      console.log(jugador);
      this.jugadores[index] = jugador;
      this.$forceUpdate();
      this.show = false;
    },
  },
};
</script>
