<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6" align="center">
       <v-img src="/logoE.png" contain  max-height="100" max-width="100" class="my-6"/>
      <v-card >
        <v-card-title class="headline">
          Welcome to the Crypto Dashboard
        </v-card-title>
  <v-autocomplete
      v-model="coins"
      :disabled="isUpdating"
      :items="coin"
      chips
      clearable
      hide-details
      hide-selected
      item-text="name"
      item-value="code"
      label="Search for a coin..."
      solo
    >
      <template v-slot:no-data>
        <v-list-item>
          <v-list-item-title>
            Search for your favorite
            <strong>Cryptocurrency</strong>
          </v-list-item-title>
        </v-list-item>
      </template>
      <template v-slot:selection="{ attr, on, item, selected }"
      >
      <router-link :to="'coins/'+item.code">
        <v-chip
          v-bind="attr"
          :input-value="selected"
          color="blue-grey"
          class="white--text"
          v-on="on"
        >
        
          <v-icon left>
            mdi-bitcoin
          </v-icon>
          <span v-text="item.name"></span>
        </v-chip>
          </router-link >
      </template>
      <template v-slot:item="{ item }"  >
        <v-list-item-avatar
          color="indigo"
          class="headline font-weight-light white--text"
        >
          {{ item.name.charAt(0) }}
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title v-text="item.name"></v-list-item-title>
          <v-list-item-subtitle v-text="item.code"></v-list-item-subtitle>
        </v-list-item-content>
        <v-list-item-action>
          <v-icon>mdi-bitcoin</v-icon>
        </v-list-item-action>
      </template>
    </v-autocomplete>
      </v-card>
    </v-col>
  </v-row>
</template>

<script lang="ts">
let cc= require('../static/cc.json')
 export default {
  head:{
    title:"main page"
    },
    data: () => ({
      coins: [],
      coin: cc,
      isUpdating: false,
      model: null,
      search: null,
      tab: null,
    }),
  }
</script>
