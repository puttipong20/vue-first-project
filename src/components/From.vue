<template>
    <v-container>
      <v-toolbar flat color="#bfe600">
        <v-icon>mdi-email</v-icon>
        <v-toolbar-title class="font-weight-light">
          Home Work Detail
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn
          color="purple darken-3"
          fab
          small
          @click="isEditing = !isEditing"
        >
          <v-icon v-if="isEditing"> mdi-close </v-icon>
          <v-icon v-else> mdi-pencil </v-icon>
        </v-btn>
      </v-toolbar>
      <v-card-text>
        <v-autocomplete
          :disabled="!isEditing"
          :items="states"
          color="black"
          item-text="name"
          label="Subject"
          v-model="From.subject"
        ></v-autocomplete>
        <v-text-field
          :disabled="!isEditing"
          color="black"
          label="Details"
          v-model="From.details"
        ></v-text-field>
        <v-text-field
          :disabled="!isEditing"
          color="black"
          label="Time to submit"
          v-model="From.time"
        ></v-text-field>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn :disabled="!isEditing" color="success" @click="save(),send()">
          Save
        </v-btn>
      </v-card-actions>
      <v-snackbar v-model="hasSaved" :timeout="2000" absolute bottom left>
        Your profile has been updated
      </v-snackbar>
    </v-container>
</template>

<script>
export default {
    name:'From',
  data() {
    return {
      hasSaved: false,
      isEditing: null,
      model: null,
      count:1,
      states: [
        { name: "web1" },
        { name: "web2" },
        { name: "web3" },
        { name: "web4" },
        { name: "web5" },
      ],
    //   รายการ
      selected: [2],
      From: {
        details: "",
        time: "",
        subject: "",
      },
      details:[
        {
          details:'',
          time:'',
          subject:'',
        }
      ]
    };
  },

  methods: {
    send(){
      this.$emit('save-data',this.details[this.count]);
      this.count++;
    },
    save() {
      this.isEditing = !this.isEditing;
      this.hasSaved = true;
      this.details.push({
        time: this.From.time,
        details: this.From.details,
        subject: this.From.subject,
      });
      this.From.details='';
      this.From.time='';
      this.From.subject='';

    },
  },
};
</script>

<style>

</style>