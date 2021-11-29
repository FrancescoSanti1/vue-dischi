<template>
    <div class="select-container">
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
    </div>
</template>

<script>
export default {
    name: 'FilteredSelection',
    props: {
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

.select-container {
    display: flex;
    justify-content: center;
    margin-bottom: 30px;
}
</style>
