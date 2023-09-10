<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <PainelCronometro @ao-controla-cronometro-finalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
    
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import PainelCronometro from './PainelCronometro.vue';

export default defineComponent({
    name: 'RegistroAtividade',
    emits: ['aoSalvarTarefa'],
    components: { PainelCronometro },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            this.$emit('aoSalvarTarefa', {
                descricao: this.descricao,
                duracaoEmSegundos: tempoDecorrido
            } )
            this.descricao = '';
        }
    }
});

</script>

<style scoped>
.formulario{
    color: var(--texto-primario);
    background: var(--bg-primario);
}
</style>