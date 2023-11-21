<template>
  <div id="search-cointainer">
    <input
      type="text"
      placeholder="Buscar tarea"
      v-model="query"
      v-on:input="$emit('query-change', query)"
    />
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      query: "",
    };
  },
};
</script>

<style scoped>
#search-container {
  width: 600px;
  margin: 0 auto;
}

input {
  border: solid 1px black;
  padding: 10px;
  width: 20%;
  outline: none;
  text-align: center;
  border-radius: 20px;
}
@media screen and (max-width: 600px) {
    input{
        width: 60%;
        }
}
</style>