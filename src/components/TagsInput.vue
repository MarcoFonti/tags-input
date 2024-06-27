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

<!-- 'KEYDOWN.ENTER' = ALL'INVIO , '$EVENT.TARGET.VALUE' = OTTINIAMO IL VALORE DELL'INPUT, 'KEYDOWN.TAB.PREVENT' = ALL'INVIO DEL TAB-->
<input type="text" :value="newTag" @keydown.enter="tags.push($event.target.value)" @keydown.tab.prevent="tags.push($event.target.value)">

</template>

<!-- CSS -->
<style scoped></style>