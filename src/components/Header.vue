<template>
    <header>
        <img src="../assets/img/logo-small.svg" alt="logo Spotify">
        <select id="filterByGenre" 
        v-model="selectedGenre" 
        @change="$emit('filter', selectedGenre)">
            <option selected value="">Tutti i generi</option>
            <option
                v-for="genre, i in list"
                :key="i"
                :value="genre">{{genre}}
            </option>
        </select>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        // questa prop riceve dal padre l'array da mostrare nel menù a tendina
        list: Array
    },
    data() {
        return {
            selectedGenre: ""
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

header {
    background-color: #2e3a46;
    height: 70px;
    padding: 0 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
        height: 40px;
    }

    select {
        padding: 5px 10px;
    }
}
</style>
