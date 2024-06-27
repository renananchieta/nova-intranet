<template>
    <v-card-text class="text-h6">Bem-vindo ao  Módulo Levantamento Necessidades Apoio</v-card-text>
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
        "title": 'Cadastrar Demanda de Pessoal', 
        "icon": 'mdi mdi-bus-school', 
        "to": "/modulos/controle-empenhos/visualizar-planilhas",
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