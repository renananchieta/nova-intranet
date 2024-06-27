<template>
    <v-card-text class="text-h6">Bem-vindo ao  Módulo Consultas Pré Matrícula</v-card-text>
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
        "title": 'Relatórios', 
        "icon": 'mdi mdi-bus-school', 
        "to": "/modulos/consultas-pre-matricula/relatorios",
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