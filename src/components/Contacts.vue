<template>
    <div class="row justify-content-center">

        <div
                v-for="contact in contacts"
                :key="contact.id"
                class="contacts"
        >
            <div class="card text-left m-3">
                <div class="card-header">
                    <h5 class="card-title">{{contact.nom}}</h5>
                    <span class="card-subtitle">{{contact.prenom}}</span>
                </div>
                <div class="card-body">
                    <span class="card-text"><b>Numéro de téléphone : </b>{{contact.telephone}}</span><br>
                    <span class="card-text"><b>Mail : </b>{{contact.mail}}</span><br>
                    <span class="card-text"><b>Date de Naissance : </b>{{contact.date_de_naissance | dateFormat }}</span><br>
                    <span class="card-text"><b>Groupe : </b>{{contact.groupe.name}}</span><br>
                    <b>Interêts : </b>
                    <ul
                            class="card-text"
                            v-for="linteret in contact.interet"
                            :key="linteret.id"
                    >
                            <li>{{linteret.name}}</li>

                    </ul>
                </div>
                <div class="card-footer">
                    <router-link :to='/contacts/+contact.id'>Voir le profil du contact</router-link>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
    const axios = require('axios');

    export default {
        name: "Contacts",
        data () {
            return {
                contacts: null,
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
        watch:{
            '$route'(to, from){

            }
        },
        mounted () {
            axios
                .get('http://localhost:8000/api/contacts')
                .then(response => (this.contacts = response.data))
        }
    }
</script>

<style scoped>

</style>