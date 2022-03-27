<template>
  <div id="nav">
        <router-link id="nav-logo" to="/">
            Julian Gojani
        </router-link>
        <div id="nav-menu">
            <router-link to="/">Home</router-link>
            <router-link to="/imprint">Imprint</router-link>
            <a href="https://github.com/julianfun123">GitHub</a>
        </div>
        <h1 style="color: #22975588; font-size: 16px; margin-top: 35px;">Blog</h1>
        <div id="posts">
            <a v-for="post of posts" :key="post.id" :href="`https://quotysco.eu/${post.blog.name}/${post.url}`">
                <h1>{{post.title}}</h1>
                <img v-if="post.image" :src="post.image">
            </a>
        </div>
    </div>
</template>
<script>
import { Prajax } from "cajaxjs";

export default {
    data: ()=>({
        posts: []
    }),
    async created(){
        console.log("YA");
        this.posts = [
            ...JSON.parse((await Prajax.get("https://quotysco.eu/api/v1/blogs/@JulianFun123/posts", {limit: 10, page: 1})).responseText).data,
            ...JSON.parse((await Prajax.get("https://quotysco.eu/api/v1/blogs/interaappsdevelopers/posts", {limit: 10, page: 1})).responseText).data.filter(p=>p.author.name == 'JulianFun123'),
            ...JSON.parse((await Prajax.get("https://quotysco.eu/api/v1/blogs/interaapps/posts", {limit: 10, page: 1})).responseText).data.filter(p=>p.author.name == 'JulianFun123')
        ].sort((a, b) => a.created_at > b.created_at ? -1 : 1 )
        console.log("YA2");
    }
}
</script>
<style lang="scss">
#nav {
    background: #0000000A;
    border-right: 2px solid #00000011;
    position: fixed;
    left: 0px;
    top: 0px;
    width: 270px;
    height: 100%;
    padding: 25px;
    overflow-x: auto;
    #nav-logo {
        font-size: 
        20px;
    }
    #nav-menu {
        margin-top: 20px;
        a {
            font-size: 17px;
            margin-top: 6px;
            display: block;

        }
    }

    #posts {
        a {
            display: block;
            padding: 0px 5px;
            margin: -5px;
            border-top: 2px solid #22975522;
            padding-bottom: 10px;
            padding-top:  10px;
            h1 {
                font-size: 16px;
            }
            img {
                max-width: 100%;
                border-radius: 10px;
            }
            &:hover {
                background: #22975509;
            }
            &:first-child {
                border-top: none;
                padding-top: 3px;
            }
        }
    }
}
</style>