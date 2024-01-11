<template>
    <v-sheet class="mx-auto" height="100vh" color="white" :style="{ 'padding': '40px' }">
        <v-card class="mx-auto my-auto" max-width="400">
            <v-container fluid>
                <v-row dense>
                    <v-col cols="12">
                        <v-text-field v-model="calcNumber" disabled step="1" label="Calculator"></v-text-field>
                    </v-col>
                    <v-col v-for="button in buttons" :key="button.item" :cols="button.col === true ? 12 : 3">
                        <v-btn :color="button.color" @click="button.function(button.item)"
                            block>{{
                                button.item }}<v-icon v-if="button.icon">{{button.icon }}</v-icon></v-btn>
                    </v-col>
                </v-row>
            </v-container>
        </v-card>
    </v-sheet>
</template>
<script>
export default {
    data() {
        return {
            buttons: [
                {
                    icon: 'mdi-backspace-outline',
                    col: true,
                    block: true,
                    color: 'grey',
                    function: this.removeNumber
                },
                {
                    item: '7',
                    function: this.addNumber
                },
                {
                    item: '8',
                    function: this.addNumber
                },
                {
                    item: '9',
                    function: this.addNumber
                },
                {
                    item: '÷',
                    function: this.addNumber,
                    color: 'orange'
                },
                {
                    item: '4',
                    function: this.addNumber
                },
                {
                    item: '5',
                    function: this.addNumber
                },
                {
                    item: '6',
                    function: this.addNumber
                },
                {
                    item: '+',
                    function: this.addNumber,
                    color: 'orange'
                },
                {
                    item: '1',
                    function: this.addNumber
                },
                {
                    item: '2',
                    function: this.addNumber
                },
                {
                    item: '3',
                    function: this.addNumber
                },
                {
                    item: '-',
                    function: this.addNumber,
                    color: 'orange'
                },
                {
                    item: '0',
                    function: this.addNumber
                },
                {
                    item: '.',
                    function: this.addNumber
                },
                {
                    item: 'AC',
                    function: this.deleteNumber
                },
                {
                    item: 'x',
                    function: this.addNumber,
                    color: 'orange'
                },
                {
                    item: '=',
                    function: this.logicalFunctions,
                    color: 'orange',
                    col: true,
                    block: true
                }],
            calcNumber: '0',

        }
    },
    methods: {
        deleteNumber() {
            this.calcNumber = '0'
        },
        addNumber(number) {
            if (['+', '-', 'x', '÷'].includes(number) && (this.calcNumber === '' || this.calcNumber === '0')) {
                return
            }
            if (['+', '-', 'x', '÷'].includes(number) && ['+', '-', 'x', '÷'].some(operator => this.calcNumber.includes(operator))) {
                return;
            }
            if (this.calcNumber === '0') {
                this.calcNumber = ''
                this.calcNumber = this.calcNumber + number
                return
            }
            this.calcNumber = this.calcNumber + number
        },
        removeNumber(){
            this.calcNumber = this.calcNumber.slice(0, -1)
        },
        logicalFunctions() {
            if (this.calcNumber.includes('+')) {
                this.sumNumbers()
                return
            }
            if (this.calcNumber.includes('-')) {
                this.subNumbers()
                return
            }
            if (this.calcNumber.includes('x')) {
                this.multNumbers()
                return
            }
            if (this.calcNumber.includes('÷')) {
                this.divNumbers()
                return
            }
        },
        sumNumbers() {
            const numbers = this.calcNumber.split('+')
            if (numbers[0] === '' || numbers[1] === '') {
                return
            }
            const number1 = parseFloat(numbers[0])
            const number2 = parseFloat(numbers[1])
            this.calcNumber = (number1 + number2) + ''
        },
        subNumbers() {
            const numbers = this.calcNumber.split('-')
            if (numbers[0] === '' || numbers[1] === '') {
                return
            }
            const number1 = parseFloat(numbers[0])
            const number2 = parseFloat(numbers[1])
            this.calcNumber = (number1 - number2) + ''
        },
        multNumbers() {
            const numbers = this.calcNumber.split('x')
            if (numbers[0] === '' || numbers[1] === '') {
                return
            }
            const number1 = parseFloat(numbers[0])
            const number2 = parseFloat(numbers[1])
            this.calcNumber = (number1 * number2) + ''
        },
        divNumbers() {
            const numbers = this.calcNumber.split('÷')
            if (numbers[0] === '' || numbers[1] === '') {
                return
            }
            const number1 = parseFloat(numbers[0])
            const number2 = parseFloat(numbers[1])
            this.calcNumber = (number1 / number2) + ''
        }
    }
}
</script>
<style scoped></style>

