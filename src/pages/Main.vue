<template>
    <q-page class="row justify-center q-gutter-y-xl">
        <div class="col-12" style="height: 35px"></div>

        <div class="col-11 col-md-10">
            <q-carousel
                arrows
                animated
                autoplay
                infinite
                v-model="slideNum"
            >
                <q-carousel-slide v-for="slide in getRecipes" :key="slide.id" :name="slide.id" :img-src="slide.img">
                    <router-link tag="div" :to="slide.url" class="absolute-bottom custom-caption">
                        <div class="text-h3">{{ slide.title }}</div>
                        <div class="text-subtitle1">{{ slide.subtitle }}</div>
                    </router-link>
                </q-carousel-slide>
            </q-carousel>
        </div>

        
        <div class="col-12 column">
            <q-card class="col-auto">
                <q-card-section class="text-h5">
                    Популярные блюда
                </q-card-section>
                <q-card-section>
                    <q-scroll-area
                        horizontal
                        style="height: 220px; width: 100%;"
                    >
                        <div class="row no-wrap q-gutter-md">
                            <router-link tag="div" :to="card.url" v-for="card in getRecipes" :key="card.id" class="col-4 col-md-3" style="width: 180px; cursor: pointer">
                                <q-card>
                                    <q-card class="my-card">
                                        <q-img :ratio="4/3" :src="card.img"/>

                                        <q-card-section class="flex" align="around">
                                            {{ card.title }}
                                        </q-card-section>
                                    </q-card>
                                </q-card>
                            </router-link>
                        </div>
                    </q-scroll-area>
                </q-card-section>
            </q-card>

            <q-card class="col-auto">
                <q-card-section class="text-h5">
                    Новинки
                </q-card-section>
                <q-card-section>
                    <q-scroll-area
                        horizontal
                        style="height: 220px; width: 100%;"
                    >
                        <div class="row no-wrap q-gutter-md">
                            <router-link tag="div" :to="card.url" v-for="card in getRecipes" :key="card.id" class="col-4 col-md-3" style="width: 180px; cursor: pointer">
                                <q-card>
                                    <q-card class="my-card">
                                        <q-img :ratio="4/3" :src="card.img"/>

                                        <q-card-section class="flex" align="around">
                                            {{ card.title }}
                                        </q-card-section>
                                    </q-card>
                                </q-card>
                            </router-link>
                        </div>
                    </q-scroll-area>
                </q-card-section>
            </q-card>

            <q-card class="col-auto">
                <q-card-section class="text-h5">
                    По категориям
                </q-card-section>
                <q-card-section>
                    <q-scroll-area
                        horizontal
                        style="height: 220px; width: 100%;"
                    >
                        <div class="row no-wrap q-gutter-md">
                            <router-link tag="div" :to="card.url" v-for="card in getRecipes" :key="card.id" class="col-4 col-md-3" style="width: 180px; cursor: pointer">
                                <q-card>
                                    <q-card class="my-card">
                                        <q-img :ratio="4/3" :src="card.img"/>

                                        <q-card-section class="flex" align="around">
                                            {{ card.title }}
                                        </q-card-section>
                                    </q-card>
                                </q-card>
                            </router-link>
                        </div>
                    </q-scroll-area>
                </q-card-section>
            </q-card>
        </div>
    </q-page>
</template>

<script>
import { mapGetters } from "vuex"
import recipes from './../components/recipes'

export default {
    computed: mapGetters(["getRecipes"]),
    data() {
        return {
            slideNum: "first"
        }
    },
    components: {
        recipes
    }
}
</script>

<style lang="stylus" scoped>
.custom-caption
  text-align center
  padding 12px
  color white
  background-color rgba(128, 128, 128, .8)
  cursor pointer
</style>
