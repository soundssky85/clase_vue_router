//import AboutPage from "@/modules/pokemon/pages/AboutPage"
//import ListPage from "@/modules/pokemon/pages/ListPage"
//import PokemonPage from "@/modules/pokemon/pages/PokemonPage"
//import NoPageFound from "@/modules/shared/pages/NoPageFound"

import {createRouter,createWebHashHistory} from "vue-router"


/* '/:pathMatch(.*)*'  Se usara para que todo aquello que vaya en una ruta distinta a las tres ya definidas redirija 
a una pagina especifica */
const routes = [
    {
        path:'/',
        redirect:'/home'
    },
    {   path: '/home', 
        name: 'home',
        component: () => import(/*webpackChunkName: "ListPage" */ "@/modules/pokemon/pages/ListPage") 
    },
    {   path: '/about', 
        name: 'about',
        component: () => import(/*webpackChunkName: "AboutPage" */  "@/modules/pokemon/pages/AboutPage")
    },
    {   
        /* path: '/:id',  */
        path: '/pokemonid/:id', 
        name: 'pokemon-id',
        component: () => import(/*webpackChunkName: "PokemonPage" */ "@/modules/pokemon/pages/PokemonPage"),
        props:(route) => {
            /* console.log(route); */
            const id = Number(route.params.id)
            return isNaN(id) ? {id:1} : {id}

            /* Si hay elementos que no se definen como properties props{} seran atributos, pero si se declaran como props, entonces pasaran a ser propiedades */
        } 
    },
    {   path: '/:pathMatch(.*)*', 
        component: () => import(/*webpackChunkName: "NoPageFound" */ "@/modules/shared/pages/NoPageFound") 
    },
]


const router = createRouter({
    // 4. Provide the history implementation to use. We are using the hash history for simplicity here.
    history: createWebHashHistory(),
    routes, // short for `routes: routes`
})


export default router
