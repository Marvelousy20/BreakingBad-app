<template>
  <q-page class="flex flex-center">
    <div>
        <q-card class="my-card" style="max-width: 400px">
            <img :src="characterData.img">

            <q-card-section>
                <div class="text-h6">{{ characterData.name }}</div>
                <div 
                class="text-subtitle2" 
                >
                    {{ characterData.nickname }}
                </div>
            </q-card-section>
            <q-card-section class="second">
               <q-chip color="teal" text-color="white" center = false size="17px" icon="bookmark"
               v-for="(occupation, index) in characterData.occupation" key="index">
                {{ occupation }}
               </q-chip>
            </q-card-section>
        </q-card>
    </div>
  </q-page>
</template>

<script>
import Axios from 'axios'
import { Loading, QSpinnerBox, QSpinnerCube, QSpinnerGears } from 'quasar'

export default {
  name: 'ProfilePage',
  data() {
    return {
        characterData: {},
    }
  },

  async created() {
    try {
        Loading.show({
        message: 'Loading',
        spinner: QSpinnerCube,
        spinnerColor: 'blue'
    })  
        let baseurl = ''
        if (this.$route.params.id === 'random') {
            baseurl = `https://www.breakingbadapi.com/api/character/${this.$route.params.id}`
        }

        else {
            baseurl = `https://www.breakingbadapi.com/api/characters/${this.$route.params.id}`
        }
        const character = await Axios.get(baseurl)

        console.log(character.data[0])   
        this.characterData = character.data[0]
        Loading.hide()
    } catch (error) {
        console.log(error)
    }
  }
}
</script>

<style scoped>
 .second {
     padding-top: 0;
 }
</style>