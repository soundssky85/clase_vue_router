<template>
    <a 
    v-if="isExternalLink" 
    target="_blank" 
    :href="link.to">{{ link.name }}</a>
    <router-link 
    v-else 
    :to="link.to"
    >{{ link.name }}</router-link>
</template>

<script>
export default {
    props:{
        link:{
            type:Object,
            required:true
        }
    },
    computed:{
        isExternalLink(){
            return this.link.to.startsWith('http')
        }
    }
}
</script>

<style>

</style>