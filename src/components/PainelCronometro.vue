<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <VisorCronometro :tempoEmSegundos="tempoEmSegundos" />
        <BotaoCronometro @clicado="iniciar" icone="fa-solid fa-play" rotulo = "Iniciar" :desabilitado="cronometroRodando"/>
        <BotaoCronometro @clicado="finalizar" icone = "fa-solid fa-stop" rotulo = "Parar" :desabilitado="!cronometroRodando"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import VisorCronometro from './VisorCronometro.vue';
import BotaoCronometro from './BotaoCronometro.vue';
export default defineComponent({
    name: 'PainelCronometro',
    components: { VisorCronometro, BotaoCronometro },
    data() {
        return {
            tempoEmSegundos: 0,
            icone: "fas fa-play",
            rotulo: "play",
            cronometroRodando: false,
            cronometro: 0
        };
    },
    methods: {
        iniciar() {
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
                this.cronometroRodando = true;
            }, 1000);
        },
        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoControlaCronometroFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    }

});

</script>
