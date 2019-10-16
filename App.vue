<template>
  <div v-highlightjs>
    <pre>
      <code class="js">
        function sum(a, b) {
          return a + b
        }
      </code>
    </pre>
  </div>
</template>

<script>
import hljs from 'highlight.js'

export default {
  directives: {
    highlightjs (el) {
      let blocks = el.querySelectorAll('pre code')
      Array.prototype.forEach.call(blocks, hljs.highlightBlock)
    }
  }
}

</script>

<style>
@import 'https://cdn.bootcss.com/highlight.js/9.12.0/styles/github.min.css'
</style>