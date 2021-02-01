<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-toolbar-title>
          Breaking Bad App
        </q-toolbar-title>
          <q-tabs
            inline-label
            class=""
          >
          <q-route-tab
           name="mails" 
           label="Andrea" 
           :to = "{name: 'profile', params: {id: 23}}"
          />
          <q-route-tab 
            name="alarms" 
            label="Christian" 
            :to = "{name: 'profile', params: {id: 4}}"
          />
          <q-route-tab 
            name="movies" 
            label="Random" 
            :to = "{name: 'profile', params: {id: 'random'}}"
          />
        </q-tabs>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view :key="$route.params.id"/>
    </q-page-container>
    
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout'
}
</script>
