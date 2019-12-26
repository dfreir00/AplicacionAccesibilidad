<template>
  <v-app id="principal">

    <v-app-bar app color="blue darken-4" dark extended Collapse-on-scroll align-center>
      <v-toolbar-title style="width: 30000px" class="ml-0 pl-4" align-center>
        <h1>Real Madrid C.F. </h1>
      </v-toolbar-title>
    </v-app-bar>
    
    <br><br><br><br><br>
    <v-card>
    <v-card-title>
      <v-spacer></v-spacer>
      Lista de partidos
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="matchs"
      :single-expand="singleExpand"
      :expanded.sync="expanded"
      :search="search"
      item-key="name"
      show-expand
      class="elevation-1"
    >
    <template v-slot:top>
      <v-toolbar  color="blue darken-4">
        <v-spacer></v-spacer>
      </v-toolbar>
    </template>
    <template v-slot:expanded-item="{ headers }" >
      
      <v-toolbar color="green" dark align='center'>
        <v-spacer></v-spacer>
            <button align-center color="white">Comprar Entradas</button>
      </v-toolbar>
      
    </template>
    <br>
    </v-data-table>
  </v-card>

  <v-card height="150">
    <v-footer
      absolute
      class="font-weight-medium"
      color="blue darken-4"
      dark
    >
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} — <strong>Real Madrid Club de Fútbol</strong>
      </v-col>
    </v-footer>
  </v-card>
  
  </v-app>
</template>

<script>
  export default {
    data () {
      
      return {
        
        expanded: [],
        sortable: false,
        singleExpand: false,
        search: '',
        headers: [
          { text: 'Rival', align: 'center', sortable: false, value: 'name', },
          { text: 'Dia', align: 'center', value: 'day' },
          { text: 'Hora', align: 'center', value: 'time' },
          { text: 'Competición', align: 'center', value: 'competition' },
          { text: '', value: 'data-table-expand' },
        ],
        matchs: [
          {
            name: 'Real Sociedad',
            day: '24-12-2019',
            time: '13:00',
            competition: 'Liga',
          },
          {
            name: 'PSG',
            day: '24-12-2019',
            time: '21:00',
            competition: 'Liga de Campeones',
          },
          {
            name: 'Viva er beti',
            day: '24-12-2019',
            time: '19:00',
            competition: 'Liga',
          },
          {
            name: 'Cultural y Deportiva Leonesa',
            day: '24-12-2019',
            time: '18:30',
            competition: 'Copa del Rey',
          },
        ],
      }
    },
  }
</script>