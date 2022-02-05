<template>
  <!-- กรอกข้อมูล -->
  <v-container>
    <v-card class="overflow-hidden" color="#f1eadc">
      <From @save-data="saveData" />
    </v-card>
    <!-- ราการการบ้าน -->
    <v-card max-width="700" class="mx-auto">
      <v-toolbar color="#bff000">
        <v-app-bar-nav-icon></v-app-bar-nav-icon>

        <v-toolbar-title>Inbox</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </v-toolbar>
      <!-- รายชื่อ -->
      <List
        class="list"
        v-for="(item, index) in Details"
        :key="index"
        :detail="Details[index]"
        :id="index"
        @deleteData="deleteDa"
      ></List>
      <!-- รายชื่อ -->
    </v-card>
    <!-- รายการการบ้าน -->
  </v-container>
</template>
<script>
import From from "../components/From.vue";
import List from "../components/List.vue";
export default {
  components: {
    From,
    List,
  },
  data: () => ({
    del:[],
    From: {
      f_details: "",
      f_time: "",
      f_subject: "",
    },
    Details: [
      {
        time: "11/22/3333",
        details: "Create web on vue",
        subject: "web 1",
      },
    ],
  }),
  methods: {
    saveData(n) {
      this.Details.push(n);
    },
    deleteDa(d){
      this.del.push(d);
      this.Details.splice(d,1);
    }
  },
};
</script>

<style>
.mx-auto {
  margin-top: 20px;
}
.BTN {
  margin: 5px 10px;
}
.overflow-hidden {
  color: black;
}
.list{
  border-bottom:2px solid black;
  margin-bottom:5px;
}
</style>
