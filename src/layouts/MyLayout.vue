<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="flex flex-center">
      <div class="cabeca">
        <div class="">
          <span class="textoInicial column">Você foi escolhido para criar um sistema para uma premiação musical.</span>
        </div>
      </div>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop
    }
  },
  methods: {
    openURL
  }
}
</script>

<style>
.cabeca{
  height: 100px;
  width: 100%;
  background: #ff4700;
}
.textoInicial{
  display: flex;
  font-family: Montserrat;
  font-style: normal;
  font-weight: bold;
  font-size: 20px;
  line-height: 24px;
  text-align: center;
  margin-top: 30px;
}
</style>
