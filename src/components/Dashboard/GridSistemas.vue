<template>
 <v-card-text class="text-h5 mx-1">
  <v-row>
    <v-col cols="12" md="8">
      Sistemas/Módulos
    </v-col>
    <v-col cols="12" md="4">
      <v-text-field
      v-model="nomeModulo"
      label="Pesquisar"
      class="text-right"
      density="compact"
      variant="underlined"
      append-inner-icon="mdi-magnify"
      @click:append-inner="pesquisarModulos()"
      hide-details
      single-line/>
    </v-col>
  </v-row>
 </v-card-text>
  <div class="px-5">
    <v-row >
        <v-col
          v-for="(sistema, i) in sistemasFiltrados"
          :key="i"
          cols="12"
          lg="3"
          md="4"
          sm="6">
          <v-hover>
            <template v-slot:default="{ isHovering, props }">
              <v-card
              v-bind="props"
              :class="{ 'on-hover': isHovering }"
              :color="isHovering ? '#0D47A1' : sistema.color"
              :elevation="isHovering ? 9 : 2"
              variant="tonal"
              :to="sistema.to">
                <v-card-item>
                  <v-row>
                    <v-col cols="6" md="7">
                      <div class="text-subtitle-1 mb-1 font-weight-bold">
                        {{ sistema.nome }}
                      </div>
                    </v-col>
                    <v-col cols="6" md="5" >
                      <v-icon :style="{ fontSize: '90px' }">
                          {{ sistema.icon }}
                      </v-icon>
                    </v-col>
                  </v-row>
                  <div>
                    <!-- <div class="text-h6 mb-1">
                        {{ sistema.nome }}
                    </div> -->
                  </div>
                </v-card-item>
                    <v-card class="centralizado py-1">
                        Acessar 
                        <v-icon>mdi-arrow-right-circle</v-icon>
                    </v-card>
              </v-card>
            </template>
          </v-hover>
        </v-col>
    </v-row>
  </div class="px-5">
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const nomeModulo = ref('');

const sistemas = ref([
  {
      nome: "Acadêmico",
      icon: "mdi mdi-town-hall",
      color: "#0097A7",
      to: "/academico",
  },
  {
      nome: "Controle de Empenhos",
      icon: "mdi mdi-currency-usd",
      color: "#0097A7",
      to: "/controle-empenhos",
  },
  {
      nome: "Levantamento Necessidades Apoio",
      icon: "mdi mdi-face-agent",
      color: "#0097A7",
      to: "/levantamento-necessidades-apoio",
  },
  {
      nome: "Pedagógico Escolas Tecnológicas",
      icon: "mdi mdi-book-edit",
      color: "#0097A7",
      to: "/pedagogico-escolas-tecnologicas",
  },
  {
      nome: "Ocorrências Escolares",
      icon: "mdi mdi-alert-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "NCOM",
      icon: "mdi mdi-account-question",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Acadêmico das EETEPAS",
      icon: "mdi mdi-chair-school",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Lotação",
      icon: "mdi mdi-account-search-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Quadro de Horários",
      icon: "mdi mdi-calendar-clock-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Segurança",
      icon: "mdi mdi-security",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Solicitação de Novas Turmas",
      icon: "mdi mdi-newspaper-plus",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Aluno Não Presencial",
      icon: "mdi mdi-map-marker-account-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "G Suíte Alunos",
      icon: "mdi mdi-google",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Matrícula",
      icon: "mdi mdi-account-plus",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Gerência Recadastramento",
      icon: "mdi mdi-account-sync-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "SIEBE",
      icon: "mdi mdi-bookshelf",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Cadastro de Vagas",
      icon: "mdi mdi-table-large-plus",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Aposentadoria",
      icon: "mdi mdi-account-clock-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Prestação de Contas",
      icon: "mdi mdi-currency-usd",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Atualização Cadastral",
      icon: "mdi mdi-file-document-refresh",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Relatórios Estratégicos",
      icon: "mdi mdi-newspaper-variant-multiple-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Configuração",
      icon: "mdi mdi-cog",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Conhecendo escola 2.0",
      icon: "mdi mdi-human-male-board-poll",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Manutenção Oferta",
      icon: "mdi mdi-office-building-cog",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "SAPP",
      icon: "mdi mdi-keyboard-settings-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Relatórios SIGEP",
      icon: "mdi mdi-newspaper-variant-outline",
      color: "#0097A7",
      to: "/manutencao",
  },
  {
      nome: "Editais",
      icon: "mdi mdi-text-box-multiple-outline",
      color: "#0097A7",
      to: "/manutencao",
  },

]);
const sistemasFiltrados = ref([...sistemas.value]);

/**
 * Methods
 */
 const pesquisarModulos = () => {
  if (nomeModulo.value.trim() === '') {
    sistemasFiltrados.value = sistemas.value;
  } else {
    sistemasFiltrados.value = sistemas.value.filter(sistema => 
      sistema.nome.toLowerCase().includes(nomeModulo.value.toLowerCase())
    );
  }
};
/**
 * Hooks
 */
</script>

<style scoped>
.centralizado{
  text-align: center;
}

.v-card {
  transition: opacity .3s ease-in-out;
}

.v-card:not(.on-hover) {
  opacity: 09;
}

.show-btns {
  color: rgba(255, 255, 255, 1) !important;
}
</style>