    <template>
        <div class="resultado" :class="resultadoClasse">
        <h3>Resultado:</h3>
        <p>{{ mensagemResultado }}</p>
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
        computed: {
        mensagemResultado() {
            if (typeof this.resultado === 'number') {
            return this.resultado;
            }
            return this.resultado || 'Aguardando cálculo...';
        },
        resultadoClasse() {
            if (typeof this.resultado === 'number') {
            return this.resultado >= 0 ? 'positivo' : 'negativo';
            }
            return 'erro';
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
        transition: background-color 0.3s, color 0.3s;
    }
    
    .resultado.positivo {
        background-color: #004f4f;
        color: #00ffbf;
    }
    
    .resultado.negativo {
        background-color: #4f0000;
        color: #ff6b6b;
    }
    
    .resultado.erro {
        background-color: #4f4f00;
        color: #ffff00;
    }
    
    @media (max-width: 768px) {
        .resultado {
        font-size: 1.2rem;
        padding: 8px;
        }
    }
    </style>  