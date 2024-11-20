<template>
    <div class="headercompo">
        <h1>
            Header component
        </h1>
        <button v-on:click=""> Home </button>
        <button v-on:click=""> Log in </button>
    </div>
</template>
  
<script>
    export default {
        name: 'HeaderCompo',
    }
</script>

<style scoped>
    .headercompo {
        height: 100px;
    }

    button {
        margin-left: 10px;
        margin-right: 10px;
    }
</style>