<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        what's up, <input type="text" placeholder=" your name" v-model="name" />
      </h2>
    </section>
  </main>
</template>

<script>
import { computed } from 'vue'
import { AppState } from './AppState'
import Navbar from './components/Navbar.vue'
import { ref, onMounted, watch } from 'vue'

const todo = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const todo_asc = computed(() => todo.value.sort((a, b) => {
  return b.createdAt - a.createdAt
}))

watch(() => name.value, (newval) => {
  localStorage.setItem('name', newval);
});
onMounted(() => {
  name.value = localStorage.getItem('name') || ''
})

// export default {
//   setup() {
//     return {
//       appState: computed(() => AppState)
//     }
//   },
//   components: { Navbar }
// }
</script>
<style lang="scss">
@import "./assets/scss/main.scss";

:root {
  --main-height: calc(100vh - 32px - 64px);
}


footer {
  display: grid;
  place-content: center;
  height: 32px;
}
</style>
