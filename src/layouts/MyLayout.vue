<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-blue-grey-14">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title>
          <q-input dark class="col-12 text-white" label="Найти блюдо" color="white">
              <template v-slot:prepend>
                  <q-icon name="search" />
              </template>
              <template v-slot:append>
                  <q-icon name="search" />
              </template>
          </q-input>
        </q-toolbar-title>

        <div>{{ getUser.name? getUser.name: "CookHub" }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
      content-class="bg-grey-2"
    >
      <q-list>
        <q-item-label header>CookHub</q-item-label>
        
        
          <q-item tag="a" active-class="bg-blue-grey-2" to="/" class="text-blue-grey" exact="">
              <q-item-section avatar>
                  <q-icon name="far fa-newspaper" />
              </q-item-section>
              <q-item-section>
                  <q-item-label>Главная</q-item-label>
              </q-item-section>
            </q-item>
        

        <q-expansion-item
          group="somegroup"
          :content-inset-level="1"
          dense-toggle
          v-model="kitchens"
          :class="{'text-blue-grey':!kitchens,'text-grey-5':kitchens}"
        >
          <template v-slot:header>
            <q-item-section avatar>
              <q-icon name="fas fa-level-up-alt"/>
            </q-item-section>
            <q-item-section>
              Уровень кухни
            </q-item-section>
          </template>

          
            <q-item tag="a" active-class="bg-blue-grey-2" class="text-blue-grey-14" v-for="kitchen in getKitchens" :key="kitchen.id" :to="'/index' + kitchen.url">
              <q-item-section>
                <q-item-label>{{ kitchen.name }}</q-item-label>
              </q-item-section>
            </q-item>
          

        </q-expansion-item>

        <q-expansion-item
          group="somegroup"
          :content-inset-level="1"
          dense-toggle
          v-model="captions"
          :class="{'text-blue-grey':!captions,'text-grey-5':captions}"
        >

          <template v-slot:header>
            <q-item-section avatar>
              <q-icon name="fas fa-flag"/>
            </q-item-section>
            <q-item-section>
              Страны и народы
            </q-item-section>
          </template>

          <q-item tag="a" active-class="bg-blue-grey-2" class="text-blue-grey-14" v-for="caption in getCaptions" :key="caption.id" :to="'/index' + caption.url">
            <q-item-section>
              <q-item-label>{{ caption.name }}</q-item-label>
            </q-item-section>
          </q-item>

        </q-expansion-item>

        <q-expansion-item
          group="somegroup"
          :content-inset-level="1"
          dense-toggle
          v-model="types"
          :class="{'text-blue-grey':!types,'text-grey-5':types}"
        >

          <template v-slot:header>
            <q-item-section avatar>
              <q-icon name="fas fa-hamburger"/>
            </q-item-section>
            <q-item-section>
              Виды блюд
            </q-item-section>
          </template>

          <q-item tag="a" active-class="bg-blue-grey-2" class="text-blue-grey-14" v-for="type in getTypes" :key="type.id" :to="'/index' + type.url">
            <q-item-section>
              <q-item-label>{{ type.name }}</q-item-label>
              <q-item-label caption>{{ type.example }}</q-item-label>
            </q-item-section>
          </q-item>
          

        </q-expansion-item>

        <q-item v-if="!getUser.name" tag="a" active-class="bg-blue-grey-2" class="text-blue-grey" to="/login">
          <q-item-section avatar>
              <q-icon name="fas fa-sign-in-alt" />
          </q-item-section>
          <q-item-section>
              <q-item-label>Вход/Регистрация</q-item-label>
          </q-item-section>
        </q-item>
        

        
        <q-item v-else tag="a" active-class="bg-blue-grey-2" class="text-blue-grey" to="/profile">
          <q-item-section avatar>
              <q-icon name="fas fa-user" />
          </q-item-section>
          <q-item-section>
              <q-item-label>Профиль</q-item-label>
          </q-item-section>
        </q-item>
        
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'
import { mapGetters } from 'vuex'

export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      kitchens: false,
      captions: false,
      types: false,
      test: ""
    }
  },
  methods: {
    openURL
  },
  computed: mapGetters(["getKitchens", "getCaptions", "getTypes", "getUser"])
}
</script>

<style>
</style>
