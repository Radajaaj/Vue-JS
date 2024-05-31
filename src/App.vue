<template>
  <div id="app">
    <img :src="bannerImage" alt="Hambuergeures ban" class="img-fluid">
    <hello></hello>
    <hr>
    <div class="d-flex justify-content-center">
      <div class="container">
        <div class="row">
          <div class="col-12 col-md-4 mb-4" v-for="item in items" :key="item.id">
            <div class="card">
              <h1 class="card-title">{{ item.title }}</h1>
              <img :src="item.image" :alt="item.alt" class="card-img-top">
              <div class="card-body">
                <p class="card-text">{{ item.description }}</p>
              </div>
              <h3 class="card-title">Quantidade:</h3>
              <contador v-model="item.quantity"></contador>
            </div>
          </div>
        </div>
      </div>
    </div>
    <hr>
    <compra
      :hamburguerQuantidade="hamburguerQuantidade"
      :cocaQuantidade="cocaQuantidade"
      :batataQuantidade="batataQuantidade"
      @resetQuantities="resetQuantities"
    ></compra>
  </div>
</template>

<script>
import hello from './components/HelloWorld.vue' //  Importamos o component do arquivo, e damos o nome de hello
import contador from './components/contador'
import compra from './components/compra'
import hamburguerCard from './assets/hamburguer_card.png'
import cocaColaCard from './assets/coca_cola_card.png'
import batataFritaCard from './assets/batata_frita_card.png'
import bannerImage from './assets/avaLanches.png'

export default {
  name: 'App',
  components: {
    hello, // Registramos o componente hello
    contador,
    compra
  },
  data () {
    return {
      bannerImage,
      items: [
        { id: 1, title: 'Hambúrguer', image: hamburguerCard, alt: 'Hamburguer saboroso', description: 'A autêntica experiência de um Hambúrguer Rústico Artesanal. Feito com um blend especial de carnes nobres, e grelhado à perfeição', quantity: 0 },
        { id: 2, title: 'Coca-Cola', image: cocaColaCard, alt: 'Coquinha gelada', description: 'Uma bebida clássica e irresistível, perfeita para acompanhar qualquer refeição. Doce, efervescente e refrescante.', quantity: 0 },
        { id: 3, title: 'Batata Frita', image: batataFritaCard, alt: 'Batata frita rústica', description: 'Cortadas em gomos generosos, temperadas com ervas finas e fritas até ficarem douradas e crocantes. Acompanha perfeitamente qualquer refeição.', quantity: 0 }
      ]
    }
  },
  computed: {
    hamburguerQuantidade () {
      return this.items.find(item => item.id === 1).quantity
    },
    batataQuantidade () {
      return this.items.find(item => item.id === 3).quantity
    },
    cocaQuantidade () {
      return this.items.find(item => item.id === 2).quantity
    }
  },
  methods: {
    resetQuantities () {
      this.items.forEach(item => { item.quantity = 0 })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.banner {
  width: 100%;
  height: auto;
}
</style>
