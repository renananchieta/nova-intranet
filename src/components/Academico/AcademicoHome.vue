<template>
    <v-card-text class="text-h6"> <v-icon>mdi mdi-town-hall</v-icon> Módulo Acadêmico </v-card-text>
</template>

<script setup>
import { onBeforeMount, onMounted, ref } from 'vue';
import { useAppStore } from '@/stores/app';
import { menuModuloAppStore } from '@/stores/menuModulo';


/**
 * Data
 */
const store = useAppStore();
const sideBarMenu = menuModuloAppStore();
const menu = ref([
    { 
        "title": 'Bora Estudar', 
        "icon": 'mdi mdi-bus-school', 
        "to": "/bora-estudar",
        "children": [],
    },
    { 
        "title": 'Diário de Classe', 
        "icon": 'mdi mdi-notebook', 
        "to": "/diario-de-classe",
        "children": [],
    },
    { 
        "title": 'Ensino Personalizado', 
        "icon": 'mdi mdi-account-star-outline', 
        "to": "/ensino-personalizado",
        "children": [],
    },
    { 
        "title": 'Matriz Curricular', 
        "icon": 'mdi mdi-note-text', 
        "to": "/matriz-curricular",
        "children": [],
    },
    { 
        "title": 'Matriz Curricular NEM', 
        "icon": 'mdi mdi-note-text', 
        "to": "/matriz-curricular-nem",
        "children": [],
    },
    { 
        "title": 'Configuração do Cadastro de Projetos NEM', 
        "icon": 'mdi mdi-cog', 
        "to": "/config-cadastro-de-projetos-nem",
        "children": [],
    },
    { 
        "title": 'PDI', 
        "icon": 'mdi mdi-cast-education', 
        "to": "/pdi",
        "children": [],
    },
    { 
        "title": 'Diário Acadêmico Digital', 
        "icon": 'mdi mdi-newspaper-variant-outline', 
        "to": "/diario-digital",
        "children": [],
    },
    { 
        "title": 'Rendimento Escolar', 
        "icon": 'mdi mdi-file-star-four-points-outline', 
        "to": "/rendimento-escolar",
        "children": [],
    },
    
]);

/**
 * Methods
 */
const getMenuModulo = () => {
    sideBarMenu.menuModulo = menu.value;
}

/**
 * Hooks
 */
onMounted(() => {
    getMenuModulo();
})

// onBeforeMount(() =>{
//     sideBarMenu.menuModulo = [];
// })
</script>