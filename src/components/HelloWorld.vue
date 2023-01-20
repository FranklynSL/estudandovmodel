<template>
  <div class="container-fluid">
    <h1>{{ msg }}</h1>
    <h2>{{ titulo }}</h2>
    <input type="text" v-model="search" placeholder="Pesquisar" />
    <div class="alert alert-warning" role="alert" v-if="usuarios.length === 0">
      Não existem registros de usuários !
    </div>
    <table class="table table-striped" v-else>
      <thead>
        <tr>
          <th>#</th>
          <th>Nome</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="usuario in usuariosFiltered" :key="usuario.id">
          <td>{{ usuario.id }}</td>
          <td>{{ usuario.nome }}</td>
          <td></td>
          <button class="btn btn-danger" @click="deletar(index)">
            Remover
          </button>
        </tr>
      </tbody>
    </table>
    <div class="form-group">
      <p></p>
      <p>
        <input
          placeholder="Digite um nome"
          type="text"
          name="nomeUsuario"
          class="from-control"
          v-model="nome"
        />
      </p>
      <button class="btn btn-primary" @click="addNewUsuario()">
        Adicionar
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data() {
    return {
      titulo: "Frangolinos",
      usuarios: [
        { id: "1", nome: "Leonardo joga barai" },
        { id: "2", nome: "Eduardo pula muro" },
        { id: "3", nome: "Gaydrigo shape inexistente" },
        { id: "4", nome: "Frankão Deus Supremo" },
        { id: "5", nome: "Thais carla moby dick" },
        { id: "6", nome: "Nina Catatau" },
        { id: "7", nome: "Champson" },
      ],
      nextUsuarioId: "8",
      id: "",
      nome: "",
      search: "",
    };
  },

  computed: {
    usuariosFiltered() {
      let valores = [];

      valores = this.usuarios.filter((usuario) => {
        return (
          usuario.nome.toLowerCase().indexOf(this.search.toLowerCase()) > -1 ||
          usuario.id.indexOf(this.search) > -1
        );
      });

      return valores;
    },
  },

  methods: {
    deletar(parametro) {
      this.usuarios.splice(parametro, 1);
    },

    addNewUsuario: function () {
      this.usuarios.push({
        id: this.nextUsuarioId++,
        nome: this.nome,
      });
      this.nome = "";
    },
  },
};
</script>

<style scoped></style>
