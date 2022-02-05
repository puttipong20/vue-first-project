<template>
  <v-container class="Lcontainer">
    <v-list three-line color="#f1eadc">
      <div>-- {{id+1}} --</div>
      <v-list-item-content>
        <v-list-item-title v-html="detail.subject"></v-list-item-title>
        <v-list-item-subtitle v-html="detail.details"></v-list-item-subtitle>
      </v-list-item-content>
    </v-list>
    <div>
      <div>{{detail.time}}</div>
      <v-btn @click="Del" color="#E3470B">Delete</v-btn>
    </div>
  </v-container>
</template>
<script>
export default {
  props: {
    detail: Object,
    id: Number
  },
  data: () => ({
    list: [],
  }),
  methods:{
    Del(){
      this.$emit('deleteData',this.id);
    }
  }
};
</script>

<style>
  .Lcontainer{
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #f1eadc;
  }
</style>
