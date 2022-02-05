<template>
  <v-app>
    <v-app-bar app color="#90fe00" dark>
      <div class="d-flex align-center but">
        HOMEWORK ! ! !
      </div>

      <v-spacer></v-spacer>

      <v-btn
        to="/"
      >
        <span class="mr-2 " >Home</span>
      </v-btn>
      <v-btn
        to="about"
      >
        <span class="mr-2">About</span>
      </v-btn>
      <v-btn
        to="todo"
      >
        <span class="mr-2">Todo</span>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
};
</script>

<style>
.but{
  color:black;
  width:100%;
  height:100%;
}
</style>
