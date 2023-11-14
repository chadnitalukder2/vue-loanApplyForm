<template>
  <Form/>
  <Table/>
</template>

<script>
import Form from './components/A_from.vue';
import Table from './components/A_Table.vue'

export default {
  name: 'App',
  components: {
    Form,
    Table
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'popines', sans-serif;
}
.app {
  width: 100%;
  margin: 0 auto;
  max-width: 80%;
  margin-top: 20px;
  text-align: center;
  background: rgb(248, 248, 248);
}

</style>
