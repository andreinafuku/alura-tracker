<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarters conteudo">
      <div class="registroAtividade">
        <RegistroAtividade @aoSalvarTarefa = "salvarTarefa"/>
      </div>
      <div class="lista">
        <RegistroTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxTarefa v-if="listaEstaVazia">
          Você não ainda não realizou tarefas hoje.
        </BoxTarefa>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import RegistroAtividade from './components/RegistroAtividade.vue';
import RegistroTarefa from './components/RegistroTarefa.vue';
import ITarefa from './interfaces/ITarefa'
import BoxTarefa from './components/BoxTarefa.vue';

export default defineComponent({
  name: 'App',
  components: { BarraLateral, RegistroAtividade, RegistroTarefa, BoxTarefa },
  data () {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia(): boolean{
      return this.tarefas.length === 0;
    }

  },
  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    }
  }
});
</script>

<style scoped>
.registroAtividade{
  margin: 1 rem;
}
.lista {
  margin: 1rem;
}
main{
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo{
  background-color: var(--bg-primario);
}
</style>