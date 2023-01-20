<template>
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
        <button class="btn btn-danger" @click="deletar(index)">Remover</button>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "ShapeInexistente",
  props: {
    usuarios: {
      type: String,
    },
  },
};
</script>

<style scoped></style>
