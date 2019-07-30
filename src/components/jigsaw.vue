<template>
  <div class="total">
    <div class="inicial">{{inicial}}</div>
    <div class="name">{{name}}</div>
  </div>
</template>

<script>
//  script
export default {
  name: 'HelloWorld',
  props: {
    inicial: String,
    name: String
  }
}
</script>

<style>
  .total{
    width: 200px;
    height: 200px;
    background-image: url('../assets/navbar-bg.png');
    background-color: #C72929;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  .total .inicial{
    font-size: 98px;
  }
  .total .name{
    font-size: 24px;
  }
</style>
