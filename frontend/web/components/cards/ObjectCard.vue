<template>
  <v-card
    v-if="orientation == 'horizontal'"
    class="object__card--horizontal"
    style="box-shadow: none"
  >
    <v-container style="">
      <v-row class="object__card__conteiner" style="">
        <v-col id="card_foto" class="" style="width:393px; margin: 0">
          <v-img
            max-width="393px"
            max-height="300px"
            lazy-src="/2.jpg"
            src="/2.jpg"
            class=""
            style="padding:0; margin:0; width: 393px!important; border-radius: 12px 0 0 12px;"
          ></v-img>
        </v-col>
        <v-col class="card__information" style="margin: 0">
          <v-card-subtitle
          class="">
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
            <v-row>
              <ul class="cards_options">
                <li>Несколько вариантов питания</li>
                <li>Горящее предложение</li>
                <li>Предоплата</li>
              </ul>
            </v-row>
          </v-card-text>
          <v-spacer></v-spacer>
          <v-card-actions
            class="object__card--horizontal__card-actions pa-0 mt-auto d-flex w-100"
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
                <span>
                  ({{ value.reviews.count }} отзывов)
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
    value: {
      type: Object,
      default: () => ({
        id: '1',
        title: 'Уютная однокомнатная квартира с видом на море',
        price: 4500,
        type: {
          id: 1,
          name: 'flat',
          title: 'квартира',
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
  methods: {},
}
</script>

<style>
.object__card--map .v-image .v-image__image--preload {
  filter: none !important;
}
.object__card__image--map .v-image .v-image__image--preload {
  filter: none !important;
}
.object__card--horizontal__card-actions {
  width: 100%;
}

.object__card--horizontal {
  width: 807px;
  height: 300px;
  border-radius: 12px;
  margin-bottom: 20px;
  border: none;
  box-shadow: none;
}

.object__card--horizontal .row {
  display: flex;
  width: 100%;
  flex-basis: auto;
  justify-content: start;
}

.v-sheet .v-card {
  border-radius: 12px;
  box-shadow: none;
}

.object__card--horizontal .container {
  padding: 0;
  width: 807px;

}



.container .row .col {
  width: 393px;
}
.row {
  margin:0;
  display: flex;
  gap: 0;
  width: 100%;

}
.col {
  padding: 0;
}

.container .object__card__conteiner {
  width: 807px;
  display: grid;
  grid-template-columns: 393px 414px;
  gap:0;
}

.container .row .card__information {
  padding: 15px 12px 12px 12px;
  width: 414px;
  height: 300px;
  border-radius: 0 12px 12px 0;
}

.container .row .card__information .v-card__subtitle {
  width: 100%;
  text-align: start;
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
  padding: 0;
  margin-bottom: 9px;
  color: #5F5F61;
}

.card__information .v-card__title {
  width: 100%;
  text-align: start;
  font-weight: 500;
  font-size: 16px;
  line-height: 20px;
  padding: 0;
  color: #37373A;
  margin-bottom: 4px;
  letter-spacing: 0.0015em;

}

.card__information__value {
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
  color: #5F5F61;
  display: flex;
  gap: 8px;
  width: 100%;
  letter-spacing: 0.004em;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 4px;
  height: 20px;
}

.card__information__options {
  height: 24px;
  display: flex;
  gap: 8px;
  width: 100%;
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
  color: #37373A;
  margin-top: 0;
  margin-bottom: 4px;

}

.row + .row {
  margin-top: 0;
}

.v-chip {
  padding-left: 6px;
  box-sizing: border-box;
}
.v-application ul {
  padding-left: 12px;

}
.cards_options {
  margin-bottom: 79px;
}
ul li {
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
  /* identical to box height, or 167% */

  letter-spacing: 0.004em;

  /* Aquamarine/100 */

  color: #00ACA2;
  list-style: disc;
}

.cards__price {
  height: 20px;
  align-items: end;
  padding-top: 3px;
  font-weight: 500;
  font-size: 16px;
  line-height: 20px;
  text-align: right;
  letter-spacing: 0.0015em;

  /* Dark Grey/100 */

  color: #37373A;

}
.cards__rating {
  display: flex;
  gap: 8px;
  align-items: end;
}
.cards__rating span{
  padding-top: 9px;
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
/* identical to box height, or 167% */

  letter-spacing: 0.004em;

/* Dark Grey/100 */

  color: #37373A;

}
.cards__rating span:last-child {
  color: #5F5F61;
}


@media screen and (max-width: 320px) {
  .row .card__information__value {
    height: 0;
  }
  .card__information__value span{
    display: none;
  }
  .v-list objects-container {
    padding-left: 0px!important;
    padding-right: 0px!important;
    padding-top: 130px!important;


  }
  .row .search__container__row .objects-container {
    padding-top: 130px!important;
    padding-left: 0!important;
    padding-right: 0!important;
  }
  .object__card__conteiner .container {
    width: 320px!important;
    margin-right: 0;
    margin-left: 0;
    padding-left: 0px!important;
    padding-right: 0px!important;
  }
  .object__card--horizontal .container {
    width: 320px;
  }
  .container .object__card__conteiner,
  .object__card__conteiner {
    width: 320px!important;
    height: 309px!important;
    grid-template-rows: 177px 132px;
    grid-template-columns: 100%;

  }

  .object__card--horizontal {
    width: 320px!important;
    height: 309px!important;
  }
  .object__card__conteiner #card_foto {
    width: 320px!important;
    height: 177px!important;
  }
  .object__card__conteiner .card__information {
    width: 320px!important;
    height: 132px!important;
    box-sizing: border-box;

  }
  .card__information .v-card__title,
  .cards__price {
    font-size: 14px;
    line-height: 18px;
  }

  #card_foto .v-responsive__content,
  #card_foto .v-responsive,
  #card_foto .v-responsive__sizer,
  #card_foto .v-image__image,
  #card_foto.v-image__image--cover {
    max-width: 320px!important;
    max-height: 177px!important;
    width: 320px !important;
    height: 177px !important;

  }

  .card__information .cards_options {
    display: none;
  }
  .card__information__options .v-chip:nth-child(3) {
    display: none;
  }
  .object__card--horizontal__card-actions,
  .v-card-actions,
  .card__information .v-application .d-flex {
    display: flex!important;
    flex-wrap: nowrap;
  }
  .container .row .card__information .v-card__subtitle {
    margin-bottom: 5px;
  }
  .container .row .card__information {
    padding: 8px
  }
  .header-filters {
    justify-content: center;
    gap: 0;
  }
}

@media screen and (min-width: 321px) and (max-width: 480px) {
  .object__card__conteiner .container {
    width: 480px!important;
    margin-right: 0;
    margin-left: 0;
    padding-left: 20px;
    padding-right: 20px;
  }
  .object__card--horizontal .container {
    width: 440px;
  }
  .container .object__card__conteiner,
  .object__card__conteiner {
    width: 440px!important;
    height: 177px!important;
    grid-template-columns: 210px 230px;

  }

  .object__card--horizontal {
    width: 440px!important;
    height: 177px!important;
  }
  .object__card__conteiner #card_foto {
    width: 210px!important;
    height: 177px!important;
  }
  .object__card__conteiner .card__information {
    width: 230px!important;
    height: 177px!important;

  }
  .card__information .v-card__title,
  .cards__price {
    font-size: 14px;
    line-height: 18px;
  }

  #card_foto .v-responsive__content,
  #card_foto .v-responsive__sizer,
  #card_foto .v-image__image,
  #card_foto.v-image__image--cover {
    width: 210px !important;
    height: 177px !important;

  }

  .card__information .cards_options {
    display: none;
  }
  .card__information__options .v-chip:nth-child(3) {
    display: none;
  }
  .object__card--horizontal__card-actions,
  .v-card-actions,
  .card__information .v-application .d-flex {
    display: block!important;
    flex-wrap: wrap;
  }
  .cards__price {
    width: 230px;
    justify-content: start!important;
    text-align: start!important;
  }
  .cards__rating {
    width: 230px;
  }
  .container .row .card__information .v-card__subtitle {
    margin-bottom: 5px;
  }
  .container .row .card__information {
    padding: 8px
    }

}
@media screen and (min-width: 481px) and (max-width: 1024px) {
  .object__card__conteiner .container {
      width: 522px!important;
      margin-right: 0;
      margin-left: 0;
      padding-left: 20px;
      padding-right: 20px;
    }

  .container .object__card__conteiner,
  .object__card__conteiner {
    width: 482px!important;
    height: 177px!important;
    grid-template-columns: 231px 251px;

  }

  .object__card--horizontal {
    width: 482px!important;
    height: 177px!important;
  }
  .object__card__conteiner #card_foto {
    width: 231px!important;
    height: 177px!important;
  }
  .object__card__conteiner .card__information {
    width: 251px!important;
    height: 177px!important;
  }

  #card_foto .v-responsive__content,
  #card_foto .v-responsive__sizer,
  #card_foto .v-image__image,
  #card_foto.v-image__image--cover {
    width: 231px !important;
    height: 177px !important;

  }

  .card__information .cards_options {
    display: none;
  }
  .container .row .card__information .v-card__subtitle {
    margin-bottom: 0;
  }

  .card__information__options .v-chip:nth-child(3) {
    display: none;
  }

  .spacer {
    display: none;
  }
  .object__card--horizontal__card-actions {
    width: 100%;
    margin-top: 15px!important;

  }
  .cards__rating span:nth-child(3) {
    display: none;
  }
  .cards__price {
font-size: 80%;
  }


}

@media screen and (min-width: 1025px) and (max-width: 1920px) {
  .object__card__conteiner .container {
    width: 812px!important;
    /*height: 250px!important;*/
    /*grid-template-columns: 296px 474px;*/
    margin-right: 0;
    margin-left: 0;
    padding-left: 20px;
    padding-right: 20px;

  }

  .container .object__card__conteiner,
  .object__card__conteiner {
    width: 772px!important;
    height: 250px!important;
    grid-template-columns: 296px 474px;

  }

  .object__card--horizontal {
    width: 772px!important;
    height: 250px!important;
  }
  .object__card__conteiner #card_foto {
    width: 296px !important;
    height: 250px !important;
  }
  .object__card__conteiner .card__information {
    width: 474px!important;
    height: 250px!important;
  }

  #card_foto .v-responsive__content,
  #card_foto .v-responsive__sizer,
  #card_foto .v-image__image,
  #card_foto.v-image__image--cover {
    width: 296px !important;
    height: 250px !important;

  }
  .card__information .v-responsive__content, .card__information .v-image__image, .card__information .v-image__image--cover {
    width: 16px!important;
    height: 16px!important;

  }
  .cards_options {
    display: block;
    margin-bottom: 0;
  }

  .cards__rating {
    margin-top: 5px;

  }
  .cards__rating span{
    padding-top: 0px;

  }
  .cards__price span {
    align-self: end;
  }
  .v-card__actions {
    padding-top: 15px!important;
  }


}


/*
по умолчанию:
@media screen and (max-width: 2500px)
*/
</style>
