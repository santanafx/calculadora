<script setup>
import { reactive } from "vue";

const estado = reactive({
    numero1: 0,
    numero2: 0,
    resultado: 0,
    operacao: "soma",
});

function operacoes(evento) {
    if (evento === "soma") {
        estado.operacao = "soma";
        estado.resultado = parseInt(estado.numero1) + parseInt(estado.numero2);
    }
    if (evento === "subtracao") {
        estado.operacao = "subtracao";
        estado.resultado = parseInt(estado.numero1) - parseInt(estado.numero2);
    }
    if (evento === "multiplicacao") {
        estado.operacao = "multiplicacao";
        estado.resultado = parseInt(estado.numero1) * parseInt(estado.numero2);
    }
    if (evento === "divisao") {
        estado.operacao = "divisao";
        estado.resultado = parseInt(estado.numero1) / parseInt(estado.numero2);
    }
}
</script>

<template>
    <section>
        <div class="container">
            <h1>Calculadora aritmética</h1>
            <label for="">Primeiro número:</label>
            <input
                @keyup="
                    (evento) => (
                        (estado.numero1 = evento.target.value),
                        operacoes(estado.operacao)
                    )
                "
                type="number"
            />
            <label for="">Segundo número:</label>
            <input
                @keyup="
                    (evento) => (
                        (estado.numero2 = evento.target.value),
                        operacoes(estado.operacao)
                    )
                "
                type="number"
            />
            <span>Selecione a operação aritmética</span>
            <select
                @change="(evento) => operacoes(evento.target.value)"
                name=""
                id=""
            >
                <option value="soma">Soma</option>
                <option value="subtracao">Subtração</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
            </select>
            <label for="">Resultado:</label>
            <input
                class="resultado"
                disabled
                type="number"
                :value="estado.resultado"
            />
        </div>
    </section>
</template>

<style scoped>
section {
    width: 100%;
    margin-top: 200px;
}
.container {
    width: 90%;
    margin: 0 auto;
    background-color: purple;
    padding: 50px;
    display: flex;
    border-radius: 20px;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}

input {
    margin-bottom: 20px;
}

select {
    margin-bottom: 20px;
}

label,
span {
    margin-bottom: 5px;
    font-weight: bold;
}

.resultado {
    background-color: white;
}
</style>
