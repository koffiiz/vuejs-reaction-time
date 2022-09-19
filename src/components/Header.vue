<template>
    <div class="header">     
       <h1> {{ gameTitle }} </h1> 
       <p> {{ gameDescription }} </p>
    </div>
</template>

<script>
    export default {
        props: [ 'gameTitle', 'gameDescription' ]
    }
</script>

<style scoped>

</style>