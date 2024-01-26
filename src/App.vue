<script setup>
import TodoApp from "./components/TodoApp.vue";
import TodoListView from "./components/TodoListView.vue";
</script>

<template>
  <html>
  <head>Title</head>
  <body>
  <header><TodoApp></TodoApp></header>
  <main><TodoListView></TodoListView></main>
  </body>
  </html>
</template>

<style scoped>
body {
    font-size: 1rem;
    font-family:sans-serif;
    width: 800px;
    height: 600px;
    display: grid;
    grid-template:
        "... ...... ..." 20px
        "... header ..." 75px
        "... ...... ..." 20px
        "... main   ..." auto
        "... ...... ..." auto
        /20px auto  20px
        ;
}
header {
    grid-area: header;
    border-radius:5%;

}
main {
    grid-area: main;
    align-self:start;
}



@media screen and (max-width: 1000px){
  body{
    grid-template:
    "header" 150px
    "main" 450px;
  }
}

</style>