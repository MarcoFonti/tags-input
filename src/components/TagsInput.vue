<!-- JS -->
<script>

export default {
    name: 'TagsInput',
    
    data() {
        return {
            tags : ["vue", "react", "angular"],
            newTag: 'Laravel'
        }
    },
};

</script>

<!-- HTML -->
<template>


<div v-for="(tag, index) in tags">{{ index + ' : ' + tag }}</div>

<hr>

{{ newTag }}

<!-- 'KEYDOWN.ENTER' = ALL'INVIO , '$EVENT.TARGET.VALUE' = OTTINIAMO IL VALORE DELL'INPUT, 'KEYDOWN.TAB.PREVENT' = ALL'INVIO DEL TAB , 'V-MODEL' = RECUPERIAMO IL VALORE INSERITO DALL'UTENTE-->
<input type="text" v-model.trim="newTag" @keydown.enter="tags.push(newTag)" @keydown.tab.prevent="tags.push(newTag)">

</template>

<!-- CSS -->
<style scoped></style>