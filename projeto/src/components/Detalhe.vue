<template>
  <section class="detalhe">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <h2>Detalhe do Produto</h2>
          <img src="../assets/red-read.jpg" alt="Red dead" />
        </div>
        <div class="col-md-9">
          <h2>Red Dead Redemption II</h2>
          <p>R$ 100,00</p>
        </div>
        <div class="col-md-3">
          <div class="detalhe__box-price">
            <p>Quantidade</p>
            <input @input="toCalculate" type="number" v-model="quantity" />
          </div>
        </div>
        <div class="col-md-12">
          <hr />
          <h3>Descrição:</h3>
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley of type
            and scrambled it to make a type specimen book. It has survived not
            only five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. Lorem Ipsum is simply dummy text of
            the printing and typesetting industry. Lorem Ipsum has been the
            industry's standard dummy text ever since the 1500s, when an unknown
            printer took a galley of type and scrambled it to make a type
            specimen book. It has survived not only five centuries, but also the
            leap into electronic typesetting, remaining essentially unchanged
          </p>
          <h4>
            Total : {{ finalQuantity }} * 100,00 =
            {{ total.toString().replace(".", ",") }}
          </h4>
        </div>
        <div class="col-md-12">
          <button @click="myFunctionDetalhe()">Fazer Pedido</button>
        </div>
        <div class="row">
          <div class="col-md-12">
            <div id="pedido">
              <NovoPedido />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import NovoPedido from "./NovoPedido.vue";

export default {
  name: "Detalhe",
  components: { NovoPedido },
  data: function() {
    return {
      quantity: 1,
      finalQuantity: 1,
      preco: 100,
      total: 0,
    };
  },
  methods: {
    toCalculate: function() {
      this.finalQuantity = this.quantity;

      if (this.quantity === "") {
        this.finalQuantity = 1;
      }

      const total = this.preco * this.finalQuantity;
      this.total = total.toFixed(2);
    },
    myFunctionDetalhe: function() {
      var id = document.getElementById("pedido");
      if (id.style.display === "none") {
        id.style.display = "block";
      } else {
        id.style.display = "none";
      }
    },
  },
};
</script>
<style>
.detalhe {
  padding: 50px 0px;
}

.detalhe img {
  margin: 20px auto;
  display: block;
}

.detalhe__box-price {
  text-align: right;
  font-weight: bold;
}

.detalhe input {
  width: 50px;
  height: 30px;
  border-radius: 4px;
  padding: 0px 8px;
}

.detalhe button {
  width: 170px;
  height: 40px;
  border-radius: 6px;
  background-color: #ae382b;
  color: #f5a022;
  border: none;
  font-weight: bold;
  display: block;
  margin: 30px auto;
}
</style>
