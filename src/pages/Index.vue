<template>
  <q-page class="flex flex-center ">
    <div class="flex-direction: cow" v-if:="$store.state.ezh.userName.length>1">
    <div >
    <h4>Привет меня зовут <br> {{$store.state.ezh.userName}}</h4>
   </div>
    <img  
    alt="hedgehog"
    src="~assets/hedgehog.png" 
    style="width: 200px; height: 200px"/>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { useStore } from 'vuex';

export default defineComponent({
  name: 'PageIndex',
  setup(){
    const $store = useStore()
    return {
      $store
    }
  }
})
</script>
