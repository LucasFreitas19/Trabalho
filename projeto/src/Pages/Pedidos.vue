<template>
  <section>
    <div class="container">
      <div class="row">
        <div class="col-md-12 list">
          <ul>
            <li v-for="pedido in pedidos" :key="pedido">
              <p>Codigo: {{ pedido.produtoId }}</p>
              <p>CPF: {{ pedido.clienteCPF }}</p>
              <p>Valor Unitario: {{ pedido.valorUnitario }}</p>
              <p>Valor Total: {{ pedido.ValorTotal }}</p>
              <p>Quantidade: {{ pedido.quantidade }}</p>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <Footer />
  </section>
</template>
<script>
import Footer from "../components/Footer.vue";

export default {
  name: "Pedidos",
  components: {
    Footer,
  },
  data: function() {
    return {
      pedidos: [],
    };
  },
  methods: {
    getPedido: async function() {
      const result = await fetch("http://localhost:3000/pedidos")
        .then((res) => res.json())
        .then((res) => res)
        .catch((error) => {
          return {
            error: true,
            message: error,
          };
        });

      if (!result.error) {
        this.pedidos = result;
      }
    },
  },
  created: function() {
    this.getPedido();
  },
};
</script>
<style>
.list li {
  border: 2px solid black;
  border-radius: 5px;
  margin: 15px;
}

.list ul {
  padding: 15px;
  list-style-type: none;
}

.list p {
  padding: 1px;
  padding-left: 10px;
}
</style>