<template>
    <v-navigation-drawer v-model="navBar" class="float-left" color="#304156" active-color="selectedColor">
        <v-sheet 
          color="#304156"
          class="pa-4 centralizado"
          position="relative">
            <v-img src="@/assets/logo_seduc_dark.png"/>
            <!-- <div class="mt-2">{{ store.usuario.nome }}</div> -->
        </v-sheet>
        <v-divider></v-divider>
        <Menu />

        <template v-slot:append>
            <v-footer color="#304156">
                <v-btn
                  block
                  class="mx-auto"
                  variant="tonal"
                  @click="logout()">
                    <v-icon icon="mr-1 mdi mdi-exit-to-app" />
                    Sair
                </v-btn>
            </v-footer>
        </template>
    </v-navigation-drawer>

    <v-app-bar :elevation="1" density="compact" color="">
        <template v-slot:prepend>
            <v-app-bar-nav-icon @click="navBar = !navBar"></v-app-bar-nav-icon>
            <v-app-bar-title>
                {{ store.usuario.nome }}
                <v-spacer></v-spacer>
            </v-app-bar-title>
        </template>
        <v-spacer></v-spacer>
        <!-- <v-expand-transition>
            <v-row>
                <v-col>
                    <v-text-field 
                    v-show="campoPesquisar == true"
                    density="compact"
                    variant="underlined"
                    label="Pesquisar"
                    color="primary"
                    class="mt-5"
                    />
                </v-col>
            </v-row>
        </v-expand-transition>
        <v-btn icon>
            <v-icon @click="campoPesquisar = !campoPesquisar">mdi-magnify</v-icon>
        </v-btn> -->
        <template v-slot:append>
            <v-menu>
                <template v-slot:activator="{ props }">
                    <v-btn 
                    icon="mdi-dots-vertical"
                    v-bind="props"></v-btn>
                </template>
                <v-list density="compact">
                    <v-list-item
                    v-for="(item, index) in items"
                    :key="index"
                    :value="index"
                    >
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </template>
    </v-app-bar>
</template>

<script setup>
import api from '@/plugins/api';
import { useAppStore } from '@/stores/app';
import { useRouter } from 'vue-router';
import Menu from './Menu.vue';
import { ref } from 'vue';

/**
 * Data
 */
const store = useAppStore();
const router = useRouter();
const navBar = ref(true);

//menu superior lado esquerdo
const items = [
    {title: "Sistemas", to: "/home"},
    {title: "Perfil", to: "/minha-conta"},
    {title: "logout", to: "/logout"}
];
const campoPesquisar = ref(false);

/**
 * Methods
 */
const logout = async() => {
    store.usuario.nome = '';

    let params = {
      headers: {
          Authorization: `Bearer ${localStorage.getItem('Authorization')}`
      }
    };

    await api.get("/logout", params)
    .then(() => {
        localStorage.clear();
        router.push("/login");
    })
    .catch((error) => {
        console.log(error);
        alert("falha de comunicação com o servidor.")
    });
}
</script>

<style scoped>
.centralizado{
  text-align: center;
}
</style>