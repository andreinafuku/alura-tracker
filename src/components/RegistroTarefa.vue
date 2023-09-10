<template>
    <BoxTarefa>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao|| "Tarefa sem descrição" }}
            </div>
            <div class="column">
                <VisorCronometro :tempo-em-segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxTarefa>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import VisorCronometro from './VisorCronometro.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxTarefa from './BoxTarefa.vue';

export default defineComponent({
    name: "RegistroTarefa",
    components: { VisorCronometro, BoxTarefa },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});
</script>

