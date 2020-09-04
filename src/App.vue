<template>
  <div id="app">
    <rsHeader/>
    <rsBody/>
    <rsFooter/>
  </div>
</template>

<script>
import rsHeader from './components/rs-header'
import rsBody from './components/rs-body'
import rsFooter from './components/rs-footer'
export default {
  name: 'App',
  components: {
    rsHeader,
    rsBody,
    rsFooter
  }
}
</script>

<style lang="scss">
body, html{
  margin: 0;
  width: 100%;
  height: 100%;
  padding: 0;
}
#app{
  width: 100%;
  height: 85%;
}
</style>
