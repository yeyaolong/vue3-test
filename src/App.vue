<template>
  <div id="app">
    <!-- <setup p1="aaaa"></setup>   -->
    <setup-2></setup-2>
    <!-- <ref-test></ref-test> -->
    <!-- <reactive-ref></reactive-ref> -->
    <!-- <to-refs></to-refs> -->
    <!-- <computed></computed> -->
    <!-- <watch-01></watch-01> -->
    <!-- <watch-02></watch-02> -->
  </div>
</template>

<script>
import Setup from './components/01setup';
import Setup2 from './components/01setup_2';
import RefTest from './components/02ref';
import reactiveRef from './components/02.1reactiveRef.vue';
import ToRefs from './components/03toRefs';
import Computed from './components/04computed';
import Watch01 from './components/05watch-01';
import Watch02 from './components/05Watch-02';
export default {
  name: 'App',
  components: {
    'setup-2': Setup2,
    Setup,
    RefTest,
    reactiveRef,
    ToRefs,
    Computed,
    'watch-01': Watch01,
    'watch-02': Watch02
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
