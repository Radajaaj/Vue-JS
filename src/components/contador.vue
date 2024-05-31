<template>
  <div class="d-flex justify-content-center align-items-center my-4">
    <b-button variant="danger" @click="menos">- 1</b-button>
    <h1 class="mx-3"> -{{ quantidade }}- </h1>
    <b-button variant="primary" @click="mais">+ 1</b-button>
  </div>
</template>

<script>
export default {
  props: {
    value: Number // Passa o valor de quantidade para as outras funções
  },
  data () {
    return {
      quantidade: this.value
    }
  },
  methods: {
    mais () {
      this.quantidade += 1
      this.$emit('input', this.quantidade)
    },
    menos () {
      if (this.quantidade > 0) {
        this.quantidade -= 1
        this.$emit('input', this.quantidade)
      }
    }
  }
}
</script>

<style>
  .counterBox {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 1%
  }
</style>
