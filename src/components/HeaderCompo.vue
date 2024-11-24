<template>
    <div class="headercompo">
        <h1>
            Header component
        </h1>
            <router-link to="/" class="button">Home</router-link>
            <router-link to="/login" class="button">Signup</router-link>
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

    .button {
        background-color:midnightblue;
        color: aliceblue;
        text-decoration: none;
        padding: 10px;
        padding-inline: 30px;
        border-radius: 20px;
        margin: 10px;
    }
</style>