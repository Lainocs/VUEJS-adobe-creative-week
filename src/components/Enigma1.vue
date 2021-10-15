<template>
    <div class="card">
        <div class="squelette">
            <!-- à remplacer par des images -->
            <p v-if="era == 'Époque victorienne'">Entrez votre code à 6 chiffes</p>
        </div>
        <div class="squelette">
            <!-- à remplacer par des images -->
            <p v-if="era == 'Années 60'">Regardez bien autour de vous</p>
        </div>
    
        <input v-if="era =='Époque victorienne'" type="text" maxlength="6" v-model="code">
        <div v-if="error == true">
            Le code de la boîte est faux
        </div>
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
                if (this.code == 841326) {
                    this.error = false
                    this.$emit('enigma', '2')
                    this.$emit('view2', false)
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

<style>
    .card {
        padding: 50px;
        background-color: rgba(322, 322, 322, 0.5);
    }
</style>