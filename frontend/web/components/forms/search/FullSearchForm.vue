<template>
  <v-toolbar-items
    app
    color="#EBEBEC"
    width="100%"
    elevation="0"
    class="header-filters"
  >
    <div class="options__wrap">
      <v-conteiner fluid class="select__wrap">
        <v-select
          v-model="filters.houseType"
          :items="houseTypes"
          multiple
          solo
          full-width
          label="Тип жилья"
          item-text="title"
          item-value="id"
          append-icon="mdi-chevron-down"
          text-color="#37373A"
          class="full_search__panel__select--house-types"
        >
          <!--      <template v-slot:selection="{ item, index }">-->
          <!--        <v-chip v-if="index < 2">-->
          <!--          <span>{{ item.title }}</span>-->
          <!--        </v-chip>-->
          <!--        <span-->
          <!--          v-if="index >= 2"-->
          <!--          class="grey&#45;&#45;text text-caption"-->
          <!--        >-->
          <!--          (и еще {{ filters.houseType.length - 2 }})-->
          <!--        </span>-->
          <!--      </template>-->
        </v-select>
        <v-select
          v-model="filters.rentalTypes"
          :items="rentalTypes"
          multiple
          solo
          full-width
          label="Тип аренды"
          item-text="title"
          item-value="id"
          append-icon="mdi-chevron-down"
          text-color="#37373A"
          class="full_search__panel__select--house-types"
        >
        </v-select>
        <v-select
          v-model="filters.price"
          :items="price"
          multiple
          solo
          full-width
          label="Цена"
          item-text="title"
          item-value="id"
          append-icon="mdi-chevron-down"
          text-color="#37373A"
          class="full_search__panel__select--house-types"
        >
        </v-select>
      </v-conteiner>
      <v-sheet elevation="0" class="chip__wrap">
        <v-chip-group v-model="filters.options" multiple class="">
          <v-chip
            v-for="item in optionsList"
            v-show="item.primary"
            :key="item.id"
            :value="item.id"

            class="header_button"
          >{{ item.title }}
          </v-chip>
        </v-chip-group>
    </v-sheet>
      <v-dialog
        v-model="advancedFiltersShow"
        persistent
        scrollable
        max-width="700px"
      >
        <template #activator="{ on, attrs }">
          <v-btn
            class="activator__button pa-4"
            text-color="#37373A"
            width="156px"
            height="56px"
            elevation="0"
            v-bind="attrs"
            v-on="on"

          >
            <v-badge
              :content="filterCount"
              :value="filterCount"
              color="primary"
              overlap
              offset-x="8"
              offset-y="5"
            >
              Все фильтры
              <v-icon>mdi-dots-vertical</v-icon>
            </v-badge>
          </v-btn>
        </template>
        <v-card>
          <v-toolbar dark color="secondary">
            <v-card-title>
              <span class="text-h5">Фильтры</span>
            </v-card-title>
          </v-toolbar>

          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12">
                  <v-card-title>Тип жилья</v-card-title>
                  <v-chip-group
                    v-model="filters.houseType"
                    column
                    multiple
                    class="ml-2 mb-4"
                  >
                    <v-chip
                      v-for="item in houseTypes"
                      :key="item.id"
                      color="primary"
                      class="advanced_filters__v-chip advanced_filters__house_type"
                      outlined
                      label
                      x-large
                      filter
                      :filter-icon="none"
                      :value="item.id"
                    >
                      {{ item.title }}
                      <v-icon right>{{ item.icon }}</v-icon>
                    </v-chip>
                  </v-chip-group>
                </v-col>
              </v-row>
              <v-divider></v-divider>
              <v-row>
                <v-col cols="12">
                  <v-card-title>Желаемая стоимость за сутки</v-card-title>
                </v-col>
              </v-row>
              <v-divider></v-divider>
              <v-row>
                <v-card-title>Удобства и опции</v-card-title>
                <v-col cols="12" md="12" class="pb-12">
                  <v-row>
                    <v-flex
                      v-for="item in optionsList"
                      :key="item.id"
                      md6
                      shrink
                      grow
                    >
                      <v-checkbox
                        v-model="filters.options"
                        :value="item.id"
                        :label="item.title"
                        color="secondary"
                        hide-details
                      ></v-checkbox>
                    </v-flex>
                  </v-row>
                </v-col>
              </v-row>
              <v-divider></v-divider>
              <v-row>
                <v-card-title>Правила проживания</v-card-title>
                <v-col cols="12" md="12">
                  <v-row>
                    <v-flex v-for="item in rules" :key="item.id" md6 shrink grow>
                      <v-checkbox
                        v-model="filters.rules"
                        :value="item.id"
                        :label="item.title"
                        color="secondary"
                        hide-details
                      ></v-checkbox>
                    </v-flex>
                  </v-row>
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions class="elevation-1">
            <v-btn
              color="secondary darken-1"
              text
              @click="advancedFiltersShow = false"
            >
              Сбросить фильтры
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn
              color="primary darken-1"
              text
              outlined
              @click="advancedFiltersShow = false"
            >
              Смотреть предложения
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>


  </v-toolbar-items>
</template>

<script>
export default {
  name: 'FullSearchForm',
  data() {
    return {
      houseTypes: [
        { id: '1', name: 'flat', title: 'Квартира', icon: 'mdi-pentagram' },
        {
          id: '2',
          name: 'room',
          title: 'Комната',
          icon: 'mdi-tag-arrow-right-outline',
        },
        { id: '33', name: 'dom', title: 'Дом', icon: 'mdi-home-outline' },
        { id: '44', name: 'hostel', title: 'Хостел', icon: 'mdi-sofa-outline' },
      ],
      rentalTypes: [
        { id: '1', name: 'daily', title: 'Посуточно' },
        { id: '2', name: 'longTime', title: 'На длительный срок' },
      ],
      price: [
        { id: '1', name: 'cheap', title: 'Дешево' },
        { id: '2', name: 'so-so', title: 'Так-сяк' },
        { id: '3', name: 'expensive', title: 'Дорого' }
      ],
      optionsList: [
        { id: '1', name: 'wifi', title: 'Бесплатная отмена', order: -1, primary: true },
        { id: '9', name: 'kam', title: 'Мгновенное подтверждение', order: 0, primary: true },
        {
          id: '2',
          name: 'cond',
          title: 'Суперхозяин',
          order: 1,
          primary: true,
        },
        {
          id: '3',
          name: 'stir',
          title: 'Горящее предложение',
          order: 2,
          primary: false,
        },
        { id: '4', name: 'utug', title: 'И ещё что-нибудь', order: 3, primary: true },
        { id: '5', name: 'fen', title: 'Что-то ещё', order: 4, primary: true },
        { id: '6', name: 'kuh', title: 'И ещё что-то длинное длинное', order: 5, primary: true }
      ],
      rules: [
        {
          id: '1',
          name: 'smoking',
          title: 'Можно курить',
          order: 0,
          primary: true,
        },
        {
          id: '2',
          name: 'smoking',
          title: 'Можно курить на балконе',
          order: 2,
          primary: true,
        },
        {
          id: '3',
          name: 'cats',
          title: 'Можно с животными',
          order: 3,
          primary: true,
        },
        {
          id: '4',
          name: 'buhlo',
          title: 'Можно бухать',
          order: 4,
          primary: true,
        },
      ],
      filters: {
        houseType: [],
        options: [],
        rules: [],
      },
      advancedFiltersShow: false,
    }
  },
  computed: {
    filterCount() {
      return this.filters.options.length + this.filters.houseType.length
    },
  },
  methods: {
    compareOptionValue(val) {
      console.log(val)
      return val
    },
  },
}
</script>

<style>/*
.v-input__slot:before {
  border: none;
}
.header-filters {
  width: 100%;
  padding-right: 274px;
  padding-left: 20px;
  padding-bottom: 22px;
  display: flex;
  justify-content: space-between;
  gap: 16px;
}
.full_search__panel__select--house-types {
  max-width: 450px;
  width: 200px;
  height: 56px;
  background-color: #FFFBF9;
  padding: 16px 20px;
  border-radius: 16px;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 0.005em;
  text-transform: none;
  color: #37373A;


  !*width: 25%;*!
}
.full_search__panel__select--house-types .v-input__slot:before,
.v-input__slot:after {
border: none!important;
}
.advanced_filters__v-chip.advanced_filters__house_type {
  width: 150px;
  text-align: center;
  justify-content: center;
  color: #37373A;

}
.select__wrap {
  display: flex;
  justify-content: space-between;
  width: 632px;
  gap: 16px;
}
.chip__wrap {
  display: flex;
  justify-content: space-between;
  width: 785px;
  align-items: center;

}
.active__chip{
  background: #E6F7F6!important;
  !* Aquamarine/80 *!

  border: 1px solid #33BDB5!important;
  opacity: 1;
}

.header_button {
  min-width: min-content;
  width: max-content;
  height: 56px;
  padding: 16px;
  background: #FFFBF9;
  border: 1px solid #D7D7D8;
  border-radius: 12px;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  !* identical to box height, or 150% *!

  letter-spacing: 0.005em;

  color: #37373A;
  text-transform: none;
  box-sizing: border-box;
  flex: 1 1 auto;
}
.header_button-active {
  background: #E6F7F6!important;
  !* Aquamarine/80 *!

  border: 1px solid #33BDB5!important;
}

.header_button:hover {
  background: #E6F7F6;
  border: 1px solid #00ACA2;
}

.header_button:focus{
  background: #FFFBF9;
  border: 2px solid #00ACA2;
}
.activator__button span {
  display: flex;
  align-items: center;
}
.activator__button {
  min-width: min-content;
  width: max-content;
  height: 56px;
  padding: 16px;
  background: #FFFBF9;
  border: 1px solid #D7D7D8;
  border-radius: 12px;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  !* identical to box height, or 150% *!

  letter-spacing: 0.005em;
box-shadow: none;
  color: #37373A;
  text-transform: none;
  box-sizing: border-box;
  flex: 1 1 auto;
  align-self: center;
}

!*.header_button-active {
  background: #E6F7F6!important;
  !* Aquamarine/80 *!
  opacity: 1!important;
  border-radius: 12px;

  border: 1px solid #33BDB5!important;
}*!

.v-chip:hover,
.activator__button:hover {
  background: #E6F7F6;
  border: 1px solid #00ACA2;
}

.options__wrap {
  width: 100%;
  align-items: center;
}
.v-chip::before {
  background-color: transparent;
}
.v-chip-group .v-slide-group__content {
   padding: 0!important;
}*/
</style>
