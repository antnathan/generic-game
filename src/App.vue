<template>
  <div id="app" class="flex col-flow stage-container">
    <div class="stage">
      <div class="header">
        <img src="./assets/logo.png" class="icon">
        <span class="title">Jogo Genérico</span>
        <div class="routes">
          <ul class="flex">
            <li v-for="(item,index) in items" :key="index" :href="item.href">{{item.name}}</li>
          </ul>
        </div>
      </div>
      <router-view/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      items: [
        {
          name: 'A',
          href: '#'
        },
        {
          name: 'B',
          href: '_blank'
        }
      ]
    }
  }
}
</script>

<style>

</style>
