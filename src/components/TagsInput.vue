<!-- JS -->
<script>

export default {
    name: 'TagsInput',

    data() {
        return {
            /* ARRAY DI PARTENZA */
            tags: ["vue", "react", "angular"],

            /* DATI CHE INSERIRA L'UTENTE */
            newTag: ''
        }
    },

    methods: {

        /* AGGIUNTA DEL NUOVO TAG */
        addNewTag() {
            if (this.newTag) {
                this.tags.push(this.newTag)

                this.newTag = ""
            }
        },

        /* RIMOVO TAG */
        removeTag(index) {
            this.tags.splice(index, 1)
        }
    },
};

</script>

<!-- HTML -->
<template>

    <!-- TAG -->
    <div v-for="(tag, index) in tags">{{ index + ' : ' + tag }}

        <!-- RIMOVI TAG -->
        <a href="#" @click.prevent="removeTag(index)">&times;</a>
    </div>

    <hr>

    <!-- NUOVO TAG -->
    {{ newTag }}

    <!-- 'KEYDOWN.ENTER' = ALL'INVIO , 
'$EVENT.TARGET.VALUE' = OTTINIAMO IL VALORE DELL'INPUT, 
'KEYDOWN.TAB.PREVENT' = ALL'INVIO DEL TAB , 
'V-MODEL' = RECUPERIAMO IL VALORE INSERITO DALL'UTENTE , 
'V-BIND:CLASSE = CI PERMETTE DI DARE UNA CLASSE DINAMICA -->
    <input type="text" v-model.trim="newTag" @keydown.enter="addNewTag" @keydown.tab.prevent="addNewTag"
        :class=" { 'tag-existing' : tags.includes(newTag) }">

</template>

<!-- CSS -->
<style scoped>
.tag-existing {
    color: red;
    text-decoration: line-through;
}
</style>