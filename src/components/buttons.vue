<template>
        <div class="btns">
        <button
            v-for="op in operacoes"
            :key="op.tipo"
            :class="['btn', { ativo: op.tipo === operacaoAtual }]"
            @click="$emit('escolher-operacao', op.tipo)"
        >
            {{ op.label }}
        </button>
        </div>
    </template>
    
    <script>
    export default {
        props: {
        operacao: {
            type: String,
            default: null,
        },
        },
        data() {
        return {
            operacoes: [
            { tipo: 'adicao', label: 'Adição' },
            { tipo: 'subtracao', label: 'Subtração' },
            { tipo: 'divisao', label: 'Divisão' },
            { tipo: 'multiplicacao', label: 'Multiplicação' },
            ],
        };
        },
    };
    </script>
    
    <style scoped>
    .btns {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        gap: 10px;
    }
    
    .btn {
        flex: 1;
        padding: 10px;
        background-color: #005f5f;
        color: white;
        border: none;
        border-radius: 5px;
        text-align: center;
        cursor: pointer;
        transition: 0.3s;
    }
    
    .btn:hover {
        background-color: #007f7f;
    }
    
    .ativo {
        background-color: #00bfbf;
    }
    </style>
  