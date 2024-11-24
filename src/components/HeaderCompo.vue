<template>
    <div class="headercompo">
        <h1>Web Application Development</h1>
        <h3>
            <router-link to="/" class="button">Home</router-link>
            Homework #3
            <router-link to="/login" class="button">Signup</router-link></h3>
    </div>
</template>
  
<script>
    export default {
        name: 'HeaderCompo',
    }
</script>

<style scoped>
    .headercompo {
        height: 140px;
        color:aliceblue;
        background: linear-gradient(0, gray, black);
        margin: 10px;
        border-radius: 10px;
        padding: 20px;
    }

    h1, h3 {
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-size-adjust: 0.7;
    }

    .button {
        background-color:midnightblue;
        color: aliceblue;
        text-decoration: none;
        font-size: small;
        padding: 10px;
        padding-inline: 30px;
        border-radius: 20px;
        margin: 10px;
    }
</style>