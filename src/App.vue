<template>
  <div id="app">
     <PageLoader />

    <router-view/>
  </div>
  
</template>

<script>

import PageLoader from './components/PageLoader'

export default {
  name: 'App',

  components: {
    PageLoader
  }
 
}
</script>

<style>
@import url('./assets/css/normalize.css');
@import url('./assets/css/estilos.css');
@import url('./assets/estilos.scss');
</style>
