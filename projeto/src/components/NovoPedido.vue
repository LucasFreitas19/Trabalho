<template>
  <section>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <h3>Novo Pedido:</h3>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
            <!-- v-model -->
          <b-input-group prepend="CPF" class="mt-3 cpf">
            <b-form-input></b-form-input>
            <button @click="myFunction" class="btn">Buscar</button>
          </b-input-group>
        </div>
      </div>
      <div class="row">
        <div class=" col-md-12">
          <div v-for="user in users" :key="user">
            <p>Nome Completo: {{ user.nome }}{{ user.sobrenome }}</p>
            <p>CPF: {{ user.cpf }}</p>
            <p>Nascimento: {{ user.dataNascimento }}</p>
          </div>
        </div>
      </div>
      <div class="row">
          <div class="col-md-12">
              <button class="btn">Salvar Pedido</button>
          </div>
      </div>
    </div>
  </section>
</template>
<script>

export default {
  name: "NovoPedido",
  data: function() {
    return {
      users: [],
    };
  },

  methods: {
    myFunction: function() {},
    getUser: async function() {
      const result = await fetch(
        "http://localhost:3000/clientes/busca/12345678912"
      )
        .then((res) => res.json())
        .then((res) => res)
        .catch((error) => {
          return {
            error: true,
            message: error,
          };
        });
      if (!result.error) {
        this.users = result;
      }

      console.log(result);
    },
  },

  created: function() {
    this.getUser();
  },
};
</script>
<style>
.btn {
  background-color: #ae382b;
  color: #f5a022;
  border: 2px solid white;
  border-radius: 10px;
  height: 10px;
}
</style>
