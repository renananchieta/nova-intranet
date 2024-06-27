<template>
    <v-card-text class="text-h6"> <v-icon>mdi mdi-town-hall</v-icon> Módulo Acadêmico </v-card-text>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue';
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
        "to": "/academico/bora-estudar",
        "children": [],
    },
    { 
        "title": 'Diário de Classe', 
        "icon": 'mdi mdi-notebook', 
        "to": "/academico/diario-de-classe",
        "children": [],
    },
    { 
        "title": 'Ensino Personalizado', 
        "icon": 'mdi mdi-account-star-outline', 
        "to": "/academico/ensino-personalizado",
        "children": [],
    },
    { 
        "title": 'Matriz Curricular', 
        "icon": 'mdi mdi-note-text', 
        "to": "/academico/matriz-curricular",
        "children": [],
    },
    { 
        "title": 'Matriz Curricular NEM', 
        "icon": 'mdi mdi-note-text', 
        "to": "/academico/matriz-curricular-nem",
        "children": [],
    },
    { 
        "title": 'Configuração do Cadastro de Projetos NEM', 
        "icon": 'mdi mdi-cog', 
        "to": "/academico/config-cadastro-de-projetos-nem",
        "children": [],
    },
    { 
        "title": 'PDI', 
        "icon": 'mdi mdi-cast-education', 
        "to": "/academico/pdi",
        "children": [],
    },
    { 
        "title": 'Diário Acadêmico Digital', 
        "icon": 'mdi mdi-newspaper-variant-outline', 
        "to": "/academico/diario-academico-digital",
        "children": [],
    },
    { 
        "title": 'Rendimento Escolar', 
        "icon": 'mdi mdi-file-star-four-points-outline', 
        "to": "/academico/rendimento-escolar",
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

// onUnmounted(() =>{
//     sideBarMenu.menuModulo = [];
// })
</script>