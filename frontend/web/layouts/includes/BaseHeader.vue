<template>

      <v-toolbar-items
        elevation="0"
        width="100%"
        color="#EBEBEC"
        class="header-search"

      >

          <v-btn
            width="64px"
            height="49px"
            icon
            class="logo__btn"
          >
            <v-icon
              width="36px"
              height="36px"
              color="rgba(0, 172, 162, 1)"
              id="menu_burger"
            >mdi-menu</v-icon>
            <v-img
              src="/LOGO.svg"
              max-height="49"
              max-width="64"
              width="64px"
              height="49px"
              id="logo"
            ></v-img>
          </v-btn>
          <v-spacer />

          <div
            class="header__date__container"
            style="width: 612px; padding: 14px 12px;">
            <div class="header__date__container-column">
              <v-img
                width="16px"
                height="16px"
                src="/search.svg"
                class="search__icon"
              ></v-img>
            </div>
            <div
              max-width="170.67px"
              width="170.67px"
              height="24px"
              class="header__date__container-column"
              >
              Ростов-на-Дону
            </div>

            <div
              max-width="1px"
              width="1px"
              height="28px"
              class="vertical__line"> </div>

            <div
              max-width="170.67px"
              width="170.67px"
              height="24px"
              class="header__date__container-column">
              26.04-01.05
            </div>

            <div
              max-width="1px"
              width="1px"
              height="28px"
              class="vertical__line"> </div>

            <div
              max-width="170.67px"
              width="170.67px"
              height="24px"
              class="header__date__container-column">
              3 гостя, 1 питомец
            </div></div>
            <small-search-form
              v-if="search"
              class="align-content-center"
              short
              hidden
            ></small-search-form>


          <v-spacer />
          <div class="btn__container">
            <v-btn
              width="186px"
              height="48px"
              text color="rgba(0, 172, 162, 1)"
              class="header__button"
            >
              Вход
            </v-btn>
            <v-btn
              width="187px"
              height="48px"
              text color="rgba(0, 172, 162, 1)"
              class="header__button">
              Регистрация
            </v-btn>
          </div>



<!--        <div class="header-filters">
          <div class="header__select">
            <v-btn width="200px" height="56px"
                   color="#FFFBF9"
                   elevation="0"
                   class="header__select__item">
              Тип жилья
              <v-icon
                width="12px"
                height="6px"
                >
                mdi-chevron-down
              </v-icon>
            </v-btn>
            <v-btn width="200px" height="56px"
                   color="#FFFBF9"
                   elevation="0"
                   class="header__select__item">
              Тип аренды
              <v-icon
                width="12px"
                height="6px"
              >
                mdi-chevron-down
              </v-icon>
            </v-btn>
            <v-btn width="200px" height="56px"
                   elevation="0"
                   color="#FFFBF9"
                   class="header__select__item">
              Цена
              <v-icon
                width="12px"
                height="6px"
              >
                mdi-chevron-down
              </v-icon>
            </v-btn>
          </div>
          <div
            max-width="1px"
            width="1px"
            height="28px"
            class="vertical__line"
          > </div>
          <div class="options__wrap">
            <v-btn
              color="#FFFBF9"
              elevation="0"
              height="56px"
              class="header_button header_button-active ma-0"
              id="btn_1">
              Бесплатная отмена
            </v-btn>
            <v-btn
              color="#FFFBF9"
              elevation="0"
              height="56px"
              class="header_button header_button-active ma-0"
              id="btn_2">
              Мгновенное подтверждение
            </v-btn>
            <v-btn
              color="#FFFBF9"
              elevation="0"
              height="56px"
                   class="header_button ma-0"
              id="btn_3">
              Суперхозяин
            </v-btn>
            <v-btn
              color="#FFFBF9"
              elevation="0"
              height="56px"
                   class="header_button ma-0"
              id="btn_4">
              Горящее предложение
            </v-btn>
            <v-btn                    color="#FFFBF9"
                                                          elevation="0"
                                                          height="56px"
                                                          class="header_button ma-0"
                                      id="btn_5">
            И ещё что-нибудь
          </v-btn>
            <v-btn                    color="#FFFBF9"
                                      elevation="0"
                                      height="56px" class="header_button ma-0"
            id="btn_6">
              Что-то ещё
            </v-btn>

            <v-btn                    color="#FFFBF9"
                                      elevation="0"
                                      height="56px"
                   class="header_button ma-0"
                                      id="btn_7">
              И ещё что-то длинное длинное
            </v-btn>
          </div>



          <div
            max-width="1px"
            width="1px"
            height="28px"
            class="vertical__line"
            id="line_hidden"> </div>

          <v-btn                    color="#FFFBF9"
                                    elevation="0"
                                    height="56px"
                                    min-width="156px"
                                    width="156px"
                                    class="header_button ma-0 header_button-active relative"
          id="filter-btn">
            Все фильтры
            <v-icon width="24px"
                    height="24px">mdi-dots-vertical</v-icon>
            <span class="check_filters_amount">3</span>
          </v-btn>

        </div>-->
      </v-toolbar-items>




</template>

<script>
/* import { mdiBiohazard } from '@mdi/js' */
import {mapGetters} from "vuex";
import SmallSearchForm from '../../components/forms/search/SmallSearchForm'
/*
import Registration from "../../components/cabinet/Registration";
import SmsConfirm from "../../components/cabinet/SmsConfirm";
import Login from "../../components/cabinet/Login";
*/


export default {
  name: 'BaseHeader',
  components: { SmallSearchForm},
  props: {
    search: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
  }),
  computed: {
    ...mapGetters({

    }),
  },
  methods: {
    toggleVisible(type, value) {

    }
  }
}
</script>

<style>
</style>
