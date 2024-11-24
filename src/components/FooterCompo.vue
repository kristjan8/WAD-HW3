<template>
    <div class="footercompo">
        <h1>
            <p>&copy; 2024 WAD Group U</p>
            <p>
                <a  target="_blank">Privacy Policy</a> | 
                <a target="_blank">Terms of Service</a>
            </p>
        </h1>
    </div>
</template>
  
<script>
    export default {
        name: 'FooterCompo',
    }
</script>

<style scoped>
    .footercompo {
        height: 50px;
    }
    .footercompo p {
        font-size: 20px; /* Make the text smaller */
        margin: 0; /* Remove default margin to keep spacing tight */
    }
    .footercompo h1{
        margin: 5px;
    }
</style>