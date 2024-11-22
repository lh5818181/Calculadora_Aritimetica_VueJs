<template>
        <div class="resultado">
        <h3>Resultado: <span>{{ resultado }}</span></h3>
        </div>
    </template>
    
    <script>
    export default {
        props: {
        resultado: {
            type: [String, Number],
            required: true,
        },
        },
    };
    </script>
    
    <style scoped>
    .resultado {
        text-align: center;
        font-size: 1.5rem;
        padding: 10px;
        background-color: #004f4f;
        color: #00ffbf;
        border-radius: 5px;
    }
    </style>  