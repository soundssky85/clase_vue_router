<template>
    <div>
        <!-- <router-link :to="{name:'home'}">Pokemon List</router-link>
        <router-link :to="{name:'pokemon-id', params:{id:78}}">Pokemon por id</router-link>
        <router-link :to="{name:'about'}">About</router-link> -->
        <CustomLink
            v-for="link in Links"
            :key="link.to"
            :link="link"
        />

        <router-link
        
        v-else
        :to="link.to"
        
        
        >
        {{ link.name }}
        </router-link> 



    </div>
</template>

<script>

import {defineAsyncComponent} from 'vue'

export default {
    data(){
        return{
            Links:[
                {to:'/',name:'Pokemons'},
                {to:'/50',name:'Por ID'},
                {to:'/about',name:'About'},
                {to:'https://google.com',name:'google'}
            ]
        }
    },
    components:{
        CustomLink: defineAsyncComponent(() => import('./CustomLink.vue'))
    }
}
</script>

<style scoped>

div{
    padding:0 30px;
}

div a{
    font-weight: bold;
    color:#2c3e50;
    margin: 0 10px;
}

/* a.router-link-exact-active{
    color: #42b983
} */
    
</style>