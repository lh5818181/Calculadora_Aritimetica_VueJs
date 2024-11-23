    <template>
        <div class="inputs">
        <label>Digite o primeiro número:</label>
        <input type="number" v-model.number="valores.num1" placeholder="Número 1" />
    
        <label>Digite o segundo número:</label>
        <input type="number" v-model.number="valores.num2" placeholder="Número 2" />
        </div>
    </template>
    
    <script>
    export default {
        props: {
        valores: {
            type: Object,
            required: true,
        },
        },
    };
    </script>
    
    <style scoped>
    .inputs {
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
    
    input {
        padding: 10px;
        font-size: 16px;
        border: 1px solid #ccc;
        border-radius: 5px;
    }
    </style>  