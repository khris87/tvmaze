<template>
    <div>
        <div class="jumbotron jumbotron-fluid text-left">
            <h1 class="display-1 pl-5">{{contact.nom}} {{contact.prenom}}</h1>
            <p class="lead pl-3">{{contact.groupe.name}} : {{contact.groupe.description}}</p>
            <hr class="my-4">
        </div>
        <div class="media w-50 mx-auto">
            <img :src="contact.groupe.logo" alt="logo de groupe">
            <div class="media-body text-left">
                <h5 class="mt-0">Détails :</h5>
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">Date de naissance : {{contact.date_de_naissance | dateFormat }}</li>
                    <li class="list-group-item">Numéro de téléphone : {{contact.telephone}}</li>
                    <li class="list-group-item">Email : {{contact.mail}}</li>
                </ul>
            </div>
        </div>
        <div
            v-for="member in contact.groupe.contacts"
            :key="member.id"
        >
            {{member.nom}}
            {{member.prenom}}
        </div>
    </div>
    
</template>

<script>
    const axios = require('axios');

    export default {
        name: "SingleContact",
        data () {
            return {
                contact: null,
                id: this.$route.params.id,
            }
        },
        filters: {
            dateFormat: function (value) {
                const date = new Date(value);
                const month = ['janvier','février','mars','avril','mai','juin','juillet','août','septembre','octobre','novembre','décembre'];
                let birth = date.getDate() + " " + month[date.getMonth()] + " " + date.getFullYear();
                return birth;
            }
        },
        mounted () {
            axios
                .get('http://localhost:8000/api/contacts/'+ this.id)
                .then(response => (this.contact = response.data))
        }
    }
</script>

<style scoped>

</style>