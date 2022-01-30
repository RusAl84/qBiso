<template>
  <q-page class="flex flex-center ">
    <q-card bordered>
    <div class="login-panel">
    <q-card-section>
      <img  
      alt="hedgehog"
      src="~assets/education.png" 
      style="width: 150px; height: 150px"/>
    </q-card-section>
    <q-card-section>
        <q-card bordered>
          <q-card-section>
            <q-input></q-input>
          </q-card-section>
          <q-card-section>
            Перевод
          </q-card-section>
        </q-card>
    </q-card-section>
    </div>
    <div>
    <q-card-section>
        <q-btn class="full-width">кнопка</q-btn>
    </q-card-section>
    </div>
    </q-card>
    
    <div v-if:="$store.state.ezh.userName.length>1">
    <div>
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
<style lang="scss" scoped>
  .login-panel{
    display: flex;
    flex-direction: row;
  }
</style>
