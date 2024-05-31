<template>
  <div class="hello">
    <h1 :title="msg">{{ msg }}</h1>
  </div>
</template>

<style>
.hello {
  background-color: whitesmoke;
}
</style>

<script>
export default{
  name: 'hello',
  data () {
    return {
      msg: 'Boas-vindas à nossa loja! Escolha o seu pedido:'
    }
  }
}
</script>
