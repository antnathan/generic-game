<template>
  <div class="flex col-flow content">
    <div class="flex">
      <!-- <full-examples/> -->
      <!-- <html-examples/> -->
      <new-example/>
    </div>
  </div>
</template>

<script>
// import htmlExamples from './htmlExamples'
import newExample from './newExample'
// import fullExamples from './fullExamples'
export default {
  name: 'HelloWorld',
  components: {
    // fullExamples
    // htmlExamples
    newExample
  },
  data () {
    return {
      items: [
        'A',
        'B'
      ]
    }
  }
}
</script>
