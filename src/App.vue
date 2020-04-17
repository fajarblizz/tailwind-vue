<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png"><img alt="Vue logo" src="./assets/tailwind1.jpg">
    <h1>TailWind</h1>

    <t-input
      :id="text.id"
      v-model="text.value"
      :disabled="text.disabled"
      :name="text.name"
    />

    <p>{{ text.value }}</p>

    <ul>
      <li>
        <label for="text-disabled">
          <input
            id="text-disabled"
            v-model="text.disabled"
            type="checkbox"
          >
          Disabled
        </label>
      </li>
    </ul>
    <p>Diatas coba pakai TailWind hahaha</p><hr>
    <hello-world/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TInput from '@/elements/TInput'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TInput
  },

  data () {
    return {
      text: {
        value: null,
        disabled: null,
        id: 'text-field',
        name: 'text-field'
      }
    }
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
