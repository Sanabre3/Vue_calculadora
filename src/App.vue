<template>
    <div class="calculator-container">
        <div class="calculator-header">
            <h1>Calculadora</h1>
            <p>Aritmética em Tempo Real</p>
        </div>

        <div class="input-group">
            <label for="number1">Primeiro Número</label>
            <input
                id="number1"
                v-model.number="number1"
                type="number"
                placeholder="Digite o primeiro número"
            />
        </div>

        <div class="input-group">
            <label for="operation">Operação</label>
            <select id="operation" v-model="operation">
                <option value="add">Adição (+)</option>
                <option value="subtract">Subtração (-)</option>
                <option value="multiply">Multiplicação (×)</option>
                <option value="divide">Divisão (÷)</option>
                <option value="modulo">Resto da Divisão (%)</option>
                <option value="power">Potência (^)</option>
            </select>
        </div>

        <div class="input-group">
            <label for="number2">Segundo Número</label>
            <input
                id="number2"
                v-model.number="number2"
                type="number"
                placeholder="Digite o segundo número"
            />
        </div>

        <div class="result-section">
            <div class="result-label">Resultado</div>
            <div class="result-value">
                {{ resultValue }}
            </div>
            <div v-if="errorMessage" class="error-message">
                {{ errorMessage }}
            </div>
        </div>

        <div class="info-message">
            O cálculo é realizado automaticamente conforme você altera os valores.
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const number1 = ref<number | null>(null)
const number2 = ref<number | null>(null)
const operation = ref<string>('add')

const errorMessage = computed(() => {
    if (operation.value === 'divide' && number2.value === 0) {
        return 'Não é possível dividir por zero'
    }
    if (operation.value === 'modulo' && number2.value === 0) {
        return 'Não é possível calcular resto com divisor zero'
    }
    return ''
})

const resultValue = computed(() => {
    if (number1.value === null || number2.value === null) {
        return '0'
    }

    if (errorMessage.value) {
        return '∞'
    }

    let result: number

    switch (operation.value) {
        case 'add':
            result = number1.value + number2.value
            break
        case 'subtract':
            result = number1.value - number2.value
            break
        case 'multiply':
            result = number1.value * number2.value
            break
        case 'divide':
            result = number1.value / number2.value
            break
        case 'modulo':
            result = number1.value % number2.value
            break
        case 'power':
            result = Math.pow(number1.value, number2.value)
            break
        default:
            result = 0
    }

    return Number.isInteger(result)
        ? result.toString()
        : result.toFixed(2).replace(/\.?0+$/, '')
})
</script>

<style scoped>
/* Estilos específicos do componente se necessário */
</style>
