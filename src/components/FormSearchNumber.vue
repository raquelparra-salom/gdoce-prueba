<template>
    <form @submit.prevent="onSubmit">
        <b-container class="bv-example-row">
            <b-row>
                <b-col> <label for="randomNumber">Introduce un número entre el 1 y el 10000000000: </label>
                </b-col>
                <b-col cols=""><input type="number" id="randomNumber" v-model="randomNumber" name="randomNumber"></b-col>
                <b-col cols="2">
                    <b-button class="play" type="submit" variant="outline-success">Play!</b-button>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <div class="input-errors" v-for="(error, index) of v$.randomNumber.$errors" :key="index">
                        <b-alert v-model="showDismissibleAlert" variant="danger" dismissible show class="error-msg">
                            {{ error.$message }}</b-alert>
                    </div>
                </b-col>
            </b-row>
        </b-container>
    </form>

    <p v-if="result >= 0">El numero es {{result}}</p>

</template>

<script>
import useVuelidate from '@vuelidate/core'
import { helpers, required, numeric, between } from '@vuelidate/validators'

export default {
    name: 'FormSearchNumber',
    setup() {
        return { v$: useVuelidate() }
    },

    data() {
        return {
            randomNumber: 0,
            maxNumber: 10000000000,
            result: -1
        }
    },

    methods: {
        onSubmit() {
            this.v$.$validate();
            if (!this.v$.$error) {
                this.result = searchNumber(this.randomNumber, this.maxNumber)
                console.log("El numero introducido es: " + this.result)
            }else {
                this.result = -1
            }
        }
    },

    validations() {
        return {
            randomNumber: {
                required: helpers.withMessage('Este campo es obligatorio', required),
                numeric: helpers.withMessage('Este campo debe ser numerico', numeric),
                between: helpers.withMessage(`El numero debe ir de 0 a ${this.maxNumber}`, between(0, this.maxNumber))
            }
        }
    }
}

function searchNumber(userNumber, maxNumber) {
    for (let i = userNumber; i <= maxNumber; i++) {
        if (i === userNumber) {
            return userNumber;
        }
    }
}

</script>

<style scoped>
input{
    width: 100%;
}
.play{
    width: 100%;
}


</style>
