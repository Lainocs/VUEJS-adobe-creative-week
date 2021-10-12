<template>
        <div class="squelette">
            <!-- à remplacer par des images -->
            <p v-if="era == 'Victorienne'">IMAGE DE SQUELETTE avec chiffres cachés '84'</p>
            <p v-if="era == 'Années 60'">IMAGE DE MANNEQUIN avec chiffres cachés '32'</p>
            <p v-if="era == 'Futur'">IMAGE DE ROBOT avec chiffres cachés '96'</p>
        </div>
    
        <input type="text" maxlength="6" v-model="code">
        <div v-if="error == true">
            Le code est faux
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
                if (this.code == 843296) {
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