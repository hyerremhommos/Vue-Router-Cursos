<template>
  <div>
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition>
      <div v-if="api" class="conteudo">
        <div>
          <h1>Sobre a {{ api.titulo }}</h1>
          <p>{{ api.descricao }}</p>

          <router-link tag="button" to="/cursos" class="btn-cursos">
            Cursos
          </router-link>

          <div>
            <h2>Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <p>{{ avaliacao.nome }}</p>
                <p>{{ avaliacao.descricao }}</p>
              </li>
            </ul>
          </div>
        </div>

        <img src="../assets/aprender.png" alt="" />
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData";

export default {
  name: "HomeView",

  mixins: [fetchData],

  created() {
    this.fetchData("/home");
  },
};
</script>

<style scoped>
.btn-cursos {
  border: none;
  background-color: #4b8;
  color: white;
  border-radius: 4px;
  cursor: pointer;
  padding: 15px 40px;
  margin-bottom: 40px;
  margin-top: 10px;
  font-size: 1rem;
  font-family: "Avenir", Arial, Helvetica, sans-serif;
  box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
}
</style>
