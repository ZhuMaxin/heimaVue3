<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

import { ref, reactive, useTemplateRef, onMounted } from 'vue'
const xypref = ref(50)
const xypreactive = reactive({ ks: 100 })

onMounted(() => {
  const refTheWelcome = useTemplateRef('refTheWelcome')
  setTimeout(()=>{
    console.log(refTheWelcome.value)
  },2000)
})

setTimeout(() => {
  xypref.value++
  xypreactive.ks++
}, 2000)
function chnagexypref(valueP) {
  xypref.value = valueP
}
</script>

<template>
  <header>
    <img
      ref="refLog"
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome
      ref="refTheWelcome"
      msg="This is a Vite + Vue 3 template."
      :xypreactive
      :xypref
      @chnagexypref="chnagexypref"
    />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
