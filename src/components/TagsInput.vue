<!-- JS -->
<script>

export default {
    name: 'TagsInput',

    data() {
        return {
            /* ARRAY DI PARTENZA */
            tags: [...this.selectedTags],

            /* DATI CHE INSERIRA L'UTENTE */
            newTag: ''
        }
    },

    /* PROPS CHE RICEVE UN ARRAY E DI DEFAULT E' UN ARRAY VUOTO */
    props : { 
        selectedTags: {
            type : Array, 
            default: () => []
        }
    },

    /* COMPUTED PER VERIFICARE CHE L'UTENTE NON INSERISCA TAG GIA' ESISTENTI */
    computed: {
        isTagExisting() {
            return this.tags.includes(this.newTag)
        }
    },

    /* EMIT */
    emit: ['change'],

    methods: {

        /* AGGIUNTA DEL NUOVO TAG */
        addNewTag() {
            if (this.newTag && !this.isTagExisting) {
                this.tags.push(this.newTag)

                this.newTag = ""

                /* RICHIAMO EMIT E PASSO COME PARAMETRO I TAGS AGGIORNATI */
                this.$emit('change', this.tags)
            }
        },

        /* RIMOVO TAG */
        removeTag(index) {
            this.tags.splice(index, 1)
            this.$emit('change', this.tags)
        }
    },
};

</script>

<!-- HTML -->
<template>

    <div class="tags-input-wrapper">

        <!-- TAG -->
        <span class="tag-item" v-for="(tag, index) in tags" :key="index">{{ index + ' : ' + tag }}

            <!-- RIMOVI TAG -->
            <a class="remove-tag" href="#" @click.prevent="removeTag(index)">&times;</a>
        </span>

        <!-- 'KEYDOWN.ENTER' = ALL'INVIO , 
            '$EVENT.TARGET.VALUE' = OTTINIAMO IL VALORE DELL'INPUT, 
            'KEYDOWN.TAB.PREVENT' = ALL'INVIO DEL TAB , 
            'V-MODEL' = RECUPERIAMO IL VALORE INSERITO DALL'UTENTE , 
            'V-BIND:CLASSE = CI PERMETTE DI DARE UNA CLASSE DINAMICA -->
        <input class="tag-input" type="text" v-model.trim="newTag" @keydown.enter="addNewTag"
            @keydown.tab.prevent="addNewTag" :class="{ 'tag-exists': isTagExisting }">

    </div>


</template>

<!-- CSS -->
<style scoped>
    .tag-input.tag-exists {
        color: red;
        text-decoration: line-through;
    }

    .tags-input-wrapper {
        background: #fff;
        padding: 0.5em;
        border: 1px solid #dbdbdb;
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        min-height: 36px;
        box-sizing: border-box;
    }

    .tag-item {
        color: #212529;
        background-color: #eee;
        margin-right: 0.3em;
        padding: 0.25em 0.4em;
        font-size: 75%;
        line-height: 1;
        text-align: center;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        padding-right: 1.25em;
        padding-left: 0.6em;
    }

    .tag-input {
        color: #495057;
        flex: 1;
        background: transparent;
        border: none;
    }

    .tag-input:focus {
        outline: none;
    }

    a.remove-tag {
        text-decoration: none;
    }
</style>