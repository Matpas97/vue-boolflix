<template>
    <header>
        <h1>Boolflix</h1>
        <div>
            <input type="text" v-model="query" @keyup.enter="$emit('search', query)"/> 
            <button @click="$emit('search', query)">Cerca</button>
        </div>       
    </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
    data(){
        return {
            query: ''
        }
    }
}
</script>

<style scoped lang="scss">
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #333;
        h1{
            color: red;
        }
    }


</style>