<template>
    <v-list
      density="compact"
    >
      <slot name="before" />
      <template
        v-for="(menu, key) in items"
        :key="key"
      >
        <v-list-group
          v-if="menu.children?.length > 0"
        >
          <template #activator="{ props }">
            <v-list-item
              :prepend-icon="menu.icon"
              exact
              v-bind="props"
              color="selectedColor"
            >
              <v-list-item-title>{{ menu.title }}</v-list-item-title>
            </v-list-item>
          </template>
          <v-list-item
            v-for="(sub, i) in menu.children"
            :key="i"
            :to="sub.to"
            color="selectedColor"
            exact
          >
            <v-list-item-title>{{ sub.title }}</v-list-item-title>
          </v-list-item>
        </v-list-group>
  
        <v-list-item
          v-else
          color="selectedColor"
          :to="menu.to"
          exact
        >
          <template #prepend>
            <v-icon :color="menu.color || ''">
              {{ menu.icon }}
            </v-icon>
          </template>
          {{ menu.title }}
        </v-list-item>
      </template>
      <slot name="after" />
    </v-list>
  </template>

<script setup>
import { useRouter } from 'vue-router';
import { useAppStore } from '@/stores/app';
import { onMounted, onUnmounted, ref } from 'vue';
import { menuModuloAppStore } from '@/stores/menuModulo';

const store = useAppStore();
const router = useRouter();
const sideBarMenu = menuModuloAppStore();
const items = ref([]);

/**
 * Methods
 */
const getMenuModulo = () => {
  items.value = sideBarMenu.menuModulo; 
}
 
/**
 * Hooks
 */
onMounted(() => {
  getMenuModulo();
});

onUnmounted(() => {
  sideBarMenu.menuModulo = [];
})

</script>

<style>

</style>