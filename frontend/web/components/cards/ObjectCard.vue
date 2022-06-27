<template>
  <v-card
    v-if="orientation == 'horizontal'"
    class="object__card--horizontal"
    style="box-shadow: none"
  >
    <v-container style="" class="pa-0">
      <v-row class="card_item__wrap pa-0" style="">
        <v-col id="card__img" class="ma-0 pa-0" style="">
          <v-img
            lazy-src="/2.jpg"
            src="/2.jpg"
            class=""
            style="border-radius: 12px 0 0 12px!important;"
          ></v-img>
        </v-col>
        <v-col class="card__information ma-0">
          <v-icon
            @click="changeColor()"
            :style="{color: this.heartColor}"
            class="cards__like">
            mdi-cards-heart-outline
          </v-icon>
          <v-card-subtitle
          class="pa-0">
          {{ value.type.title }}
          </v-card-subtitle>
          <v-card-title
            class=""
            style=""
          >
            {{ value.title }}
          </v-card-title>
          <v-card-text class="ml-0 pa-0">
            <v-row class="card__information__value">
              <span class="">
                4 гостя
              </span>
              <span class="">
                2 кровати
              </span>
              <span class="">
                1 спальня
              </span>
              <span class="">
                {{ square }} м<sup>2</sup>
              </span>

            </v-row>
            <v-row class="card__information__options">
              <v-chip
                v-for="item in value.options"
                v-show="item.primary"
                :key="item.id"
                outlined
                small
                :value="item.id"
                class=""
              >
                <v-img :src="item.img" style="width: 16px; height: 16px; margin-right: 6px;"></v-img>

                {{ item.title }}
              </v-chip>
            </v-row>
            <v-row class="ma-0">
              <ul class="cards_options">
                <li>Несколько вариантов питания</li>
                <li>Горящее предложение</li>
                <li>Предоплата</li>
              </ul>
            </v-row>
          </v-card-text>

          <v-card-actions
            class="object__card--horizontal__card-actions pa-0 d-flex w-100"
          >
            <v-flex class="d-inline-flex align-center">

              <div class="cards__rating">
                <v-img
                min-width="25px"
                max-width="25px"
                lazy-src="/Star.svg"
                src="/Star.svg"
                class="align-self-center"
              ></v-img>
                <span>
                  {{ value.rating.value }}
                </span>
                <span class="cards__reviews">
                  ({{ value.reviews.count }}<span class="cards__reviews-text"> отзывов</span>)
                </span>

              </div>
            </v-flex>
            <v-flex class="text--darken-2 text-right cards__price">
              <span>от {{ value.price | currency }} / ночь</span>
            </v-flex>
          </v-card-actions>
        </v-col>
      </v-row>
    </v-container>
  </v-card>

</template>

<script>
import collect from 'collect.js'

export default {
  name: 'ObjectCard',
  props: {
    orientation: {
      // horizontal || vertical
      type: String,
      default: 'horizontal',
    },
    data () {
      return {
        heartColor: 'rgba(255, 251, 249, 0.6)'
      }
    },
    value: {
      type: Object,
      default: () => ({
        id: '1',
        title: 'Уютная однокомнатная квартира с видом на море',
        price: 4500,
        type: {
          id: 1,
          name: 'flat',
          title: 'Квартира',
        },
        params: [
          { id: '1', name: 'square', title: 'Площадь', value: '40' },
          { id: '2', name: 'rooms', title: 'Количество комнат', value: '2' },
          {
            id: '3',
            name: 'max_guests',
            title: 'гостя',
            value: '4',
          },
        ],
        options: [
          {
            id: '1',
            name: 'wifi',
            title: 'WI FI',
            order: 0,
            primary: true,
            img: '/Wi-Fi.svg',
            icon: 'mdi-rss',
          },
          {
            id: '2',
            name: 'pets',
            title: 'Pets friendly',
            order: 1,
            primary: true,
            img: '/Wave.svg',
            icon: 'mdi-waves',
          },
          {
            id: '3',
            name: 'abort',
            title: 'Бесплатная отмена',
            order: 2,
            primary: true,
            img: '/Line.svg',
            icon: 'mdi-cloud-refresh',
          },
          /* {
            id: '2',
            name: 'cond',
            title: 'Кондиционер',
            order: 1,
            primary: true,
            icon: 'mdi-cloud-refresh',
          },
          {
            id: '3',
            name: 'stir',
            title: 'Стиральная машина',
            order: 2,
            primary: true,
            icon: 'mdi-compass-rose',
          },
          {
            id: '4',
            name: 'utug',
            title: 'Утюг',
            order: 3,
            primary: true,
            icon: 'mdi-toilet',
          } */
        ],
        rating: {
          value: 4.75,
          detail: {},
        },
        reviews: {
          count: 8,
          list: [],
        },
      }),
    },
    map: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    /**
     * Collection of the value
     * @return {Collection<unknown>}
     */
    val() {
      return collect(this.value)
    },
    params() {
      return collect(this.val.get('params')).keyBy('name')
    },
    square() {
      return this.params.get('square').value
    },
    rooms() {
      return this.params.get('rooms').value
    },
    maxGuests() {
      return this.params.get('max_guests').value
    },
  },
  methods: {
    changeColor() {
      this.heartColor = this.heartColor === 'rgba(255, 251, 249, 0.6)' ? '#FF5252' : 'rgba(255, 251, 249, 0.6)'
    }

  },
}
</script>

<style>
</style>
