<template>
    LE PENDU AVEC LE MOT SQUELETTE
    <input type="text" v-model="result">
    <div v-if="error == true">
        Le mot est faux
    </div>
</template>

<script>
    export default {
        name: 'Hangman',
        props: [
            'era'
        ],
        data() {
            return {
                result : '',
                error: false,
            }
        },
        methods: {
            verifyResult() {

                let result = this.result.toLowerCase()

                if (result == 'squelette') {
                    this.error = false
                    this.$emit('enigma', '1')
                } else {
                    this.error = true
                }
            }
        },
        watch: {
            result() {
                if(this.result.length == 9) {
                    this.verifyResult()
                }
            }
        }
    }
</script>