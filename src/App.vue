<script setup>
import Table from './components/Table/Table.vue'
import database from './database/data.json';
import { ref } from 'vue'

const databaseRework = ref( database.map( client => {
  client.dates = client.dates.map( date => {
    date.start_date  = new Date(date.start_date);
    date.end_date = new Date(date.end_date);
    return date
  });
  client.status = client.dates.map ( date => {
    let nowToEnd = Math.floor( (new Date() - date.end_date)/86400000 );
    let nowToStart = Math.floor( (new Date() - date.start_date)/86400000 );
    return {
      done: nowToEnd > 0,
      days: nowToStart > 0 ? nowToEnd : -nowToStart
    }    
  })
  return client;
}))

function test () {
  databaseRework.value.sort( (a,b) => a.o_id - b.o_id);
}


</script>

<template>
    <!-- <TheWelcome /> -->
    <Table :databaseOfClients = databaseRework @sortID="test"></Table>
</template>

