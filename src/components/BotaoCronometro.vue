<template>
    <button class="button" @click="clicado" :disabled="desabilitado">
        <span class="icon">
            <i :class=icone></i>
        </span>
        <span>{{rotulo}}</span>
    </button>

</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BotaoCronometro',
    emits: ['clicado'],
    props: {
        icone: {
            type: String,
            required: true
        },
        rotulo: {
            type: String,
            required: true
        },
        desabilitado: {
            type: Boolean
        }
    },
    methods:{
        clicado():void {
            this.$emit('clicado');
        }
    }
});
</script>