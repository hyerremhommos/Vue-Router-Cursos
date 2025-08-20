<template>
  <div>
    <div v-if="loading">
      <PageLoading />
    </div>

    <transition>
      <div v-if="api">
        <h1>{{ api.titulo }}</h1>
        <p>{{ api.descricao }}</p>
        <ul>
          <li>
            <p><strong>Email:</strong> {{ api.contato.email }}</p>
          </li>

          <li>
            <p><strong>Telefone:</strong> {{ api.contato.telefone }}</p>
          </li>

          <li>
            <p><strong>Endereço:</strong> {{ api.contato.endereco }}</p>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData";

export default {
  name: "ContatoView",

  mixins: [fetchData],

  created() {
    this.fetchData("/contato");
  },
};
</script>

<style></style>
