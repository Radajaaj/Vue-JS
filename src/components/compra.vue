<template>
  <div :class="cardClass">
    <div class="card-body">
      <h5 class="card-title">TOTAL DA COMPRA</h5>
      <hr>
      <p class="card-text">Hamburguer: {{ hamburguerQuantidade }} x R$ 19,99 = {{ hamburguerTotal.toFixed(2) }}</p>
      <p class="card-text">Batata frita: {{ batataQuantidade }} x R$ 9,99 = {{ batataTotal.toFixed(2) }}</p>
      <p class="card-text">Coca-Cola: {{ cocaQuantidade }} x R$ 5,99 = {{ cocaTotal.toFixed(2) }}</p>
      <hr>
      <p class="card-text">TOTAL: R$ {{ total.toFixed(2) }}</p>
      <hr>
      <a href="#" class="btn btn-primary" @click="notaFiscal">Finalizar compra!</a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    hamburguerQuantidade: Number,
    batataQuantidade: Number,
    cocaQuantidade: Number
  },
  data () {
    return {
      isSmallScreen: window.innerWidth <= 768
    }
  },
  computed: {
    cardClass () {
      return this.isSmallScreen ? 'card' : 'card fixed-card'
    },
    hamburguerTotal () {
      return this.hamburguerQuantidade * 19.99
    },
    batataTotal () {
      return this.batataQuantidade * 9.99
    },
    cocaTotal () {
      return this.cocaQuantidade * 5.99
    },
    total () {
      return this.hamburguerTotal + this.batataTotal + this.cocaTotal
    }
  },
  methods: {
    notaFiscal () {
      this.$emit('resetQuantities')
    },
    updateScreenSize () {
      this.isSmallScreen = window.innerWidth <= 1768
    }
  },
  mounted () {
    window.addEventListener('resize', this.updateScreenSize)
  },
  beforeDestroy () {
    window.removeEventListener('resize', this.updateScreenSize)
  }
}
</script>

<style>
.fixed-card {
  position: fixed;
  top: 50%; /* Ajuste o valor para mudar a posição vertical */
  right: 0.2%; /* Ajuste o valor para mudar a posição horizontal */
  transform: translateY(-50%);
}
</style>
