<template>
    enigme 1
        <input type="text" maxlength="6" v-model="code">
        <div v-if="error == true">
            Le code est faux
        </div>
        <div v-if="era == 'Futur'">
            la code est 150101
        </div>
</template>

<script>
    export default {
        name: 'Enigma1',
        props: [
            'era'
        ],
        data() {
            return {
                code : '',
                error: false,
            }
        },
        methods: {
            verifyCode() {
                if (this.code == 150101) {
                    this.error = false
                    this.$emit('enigma', '2')
                } else {
                    this.error = true
                }
            }
        },
        watch: {
            code() {
                if(this.code.length == 6) {
                    this.verifyCode()
                }
            }
        }
    }
</script>