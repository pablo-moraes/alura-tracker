<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode':darkMode}">
    <div class="column is-one-quarter">
      <barra-lateral @onAlterTheme="alterTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <formulario @onSaveTask="saveTask"/>
      <!-- Lista de tarefas -->
      <div class="lista">
        <tarefa v-for="(tarefa, index) in tarefas" :key="index"  :tarefa="tarefa" />
        <box v-if="emptyList" class="has-text-centered py-2">
          Você não tem nenhuma tarefa ainda meu parsa :(
        </box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import BarraLateral from '@/components/BarraLateral.vue'
import Formulario from '@/components/Formulario.vue'
import Tarefa from '@/components/Tarefa.vue'
import Box from '@/components/Box.vue'
import ITarefa from '@/interfaces/ITarefa'

import '@fortawesome/fontawesome-free/css/all.css'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data () {
    return {
      tarefas: [] as ITarefa[],
      darkMode: false
    }
  },
  computed: {
    emptyList () :boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    saveTask (tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    alterTheme (darkModeActive: boolean) : void {
      this.darkMode = darkModeActive
    }
  }
});
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

main {
  --bg-primary: #fff;
  --text-color: #000;
}

main.dark-mode {
  --bg-primary: #2b2d42;
  --text-color: #fff;
}

.content {
  background: var(--bg-primary);
  color: var(--text-color);
}
</style>
