<template>
    <div class="contentcompo">
        <p class="posts" v-for="post in postsList" :key="post.id">
            <table width="100%">
                <tr>
                    <td>{{post.username}}</td>
                    <td style="text-align: right">{{post.datetime}}</td>
                </tr>
            </table>
            <img v-if="post.image !== ''" :src="post.image">
            <br>
            {{post.text}}
            <table width="100%">
                <tr>
                    <td><img src="../assets/like.png" height="25" width="25" @click="likePost(post.id)" style="cursor: pointer;"></td>
                    <td style="text-align:right">{{post.likes}} likes</td>
                </tr>
            </table>
        </p>
        <button v-on:click="resetLikes()"> Reset likes </button>
    </div>
</template>
  
<script>
    export default {
        name: 'ContentCompo',
        data: function() {
            return {
            }},
        computed: {
            postsList(){
                return this.$store.state.postsList
            }
        },
        methods: { 
            likePost(postId) { 
                this.$store.dispatch('incrementLikes', postId); 
            },
            resetLikes() { 
                this.$store.dispatch('resetLikes'); 
            } 
        }
    }
</script>

<style scoped>
    .contentcompo {
        background-color: transparent;
        width: 60%;
        height: 100%;
    }

    .posts {
        background-color: lightgray;
        border-radius: 10px;
        padding: 10px;
        margin-left: 10px;
        margin-right: 10px;
        text-align: left;
    }

    button {
        background-color: darkred;
        color: aliceblue;
        padding: 10px;
        padding-inline: 30px;
        border-radius: 20px;
        cursor: pointer;
    }
    button:hover {
    background-color: #45a049; /* Change background color on hover */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); /* Optional: Add a shadow on hover */
    }
</style>