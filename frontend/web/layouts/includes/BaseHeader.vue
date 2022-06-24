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
<!--          <v-spacer />-->
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
            </div>
            <small-search-form
              v-if="search"
              class="align-content-center"
              short
              hidden
            ></small-search-form>
          </div>

<!--          <v-spacer />-->
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

.v-toolbar__content, .v-toolbar__extension{

  display: flex!important;
  flex-direction: column!important;
  padding: 0;


}

.header-search {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 0px;
}

.header-search .col {
  padding: 14px 12px;
  max-width: 612px;
}

.header__date__container {
  width: 612px;
  height: 52px;
  background-color: rgba(255,251,249,1);
  padding: 14px 12px;
  margin: 22px 0 28px 0;
  border-radius: 12px;
  border: none;
  box-sizing: border-box;
  display: grid;
  grid-template-columns: 16px 170.67px 1px 170.67px 1px 170.67px;
  gap: 12px;
/*  display: flex;
  justify-content: space-between;
  gap:0;*/

}

.header__date__container .col {

}

.header-search .col .col {
  padding: 0;

}




.header__date__container-column {
  text-align: center;
  width: 170.67px;
  color: rgba(55, 55, 58, 1);
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
}

.vertical__line {
  background-color: rgba(175, 175, 176, 1);
  border-left: 1px solid #AFAFB0;
}

.search__icon {
  margin-top: 4px;
  margin-bottom: 4px;
}


.logo__btn {
  margin: 26px 860px 27px 26px;
}
.header__button {
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  text-align: center;
  border-radius: 16px;
  border: 1px solid #00ACA2;
  background-color: rgba(255, 251, 249, 0.6);
  box-sizing: border-box;
  text-transform: none;

}

.btn__container {
  margin-left: 531px;
  display: flex;
  gap: 20px;
  margin-top: 21px;
  margin-bottom: 33px;
  margin-right: 20px;
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
  /* identical to box height, or 150% */

  letter-spacing: 0.005em;

  color: #37373A;
  text-transform: none;
  box-sizing: border-box;
  flex: 1 1 auto;
}

.header_button-active {
  background: #E6F7F6!important;
  /* Aquamarine/80 */

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

.header_button:first-child {
  margin-right: 20px;
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

.header__select {
  gap: 16px;
  display: flex;
  justify-content: space-between;
}

.header__select__item {
  display: flex;
  justify-content: space-between;
  padding: 16px 20px;
  border-radius: 16px;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 0.005em;
  text-transform: none;

  color: #37373A;

}

.options__wrap {
  display: flex;
  width: 100%;
  justify-content: space-between;
  flex-wrap: nowrap;
  gap: 4px;
}
.relative {
  position: relative;
}

.relative .v-btn__content {
  position: static;
}
.check_filters_amount {
  position: absolute;
  top: -3.27px;
  right: -4px;
  width: 20px;
  height: 20px;
  background: #33BDB5;
  border-radius: 40px;
  display: flex;
  align-items: center;
  letter-spacing: 0.004em;
  justify-content: center;
  color: #FFFBF9;
}
@media screen and (max-width: 320px) {
  #app__header {
    width: 320px;
    height: 130px!important;
  }

  #menu_burger {
    display: flex;
    width: 36px;
    height: 36px;

  }

  .logo__btn {
    margin-right: 10px !important;
    margin-left: 12px !important;
    width: 36px !important;
    height: 36px !important;
  }

  #logo {
    display: none;
  }
  #btn_1,
  #btn_2,
  #btn_3, #btn_4,
  #btn_5, #btn_6, #btn_7, #line_hidden,
  .header__select,
  .header-filters .vertical__line {
    display: none;

  }
  .btn__container,
  .btn__container button{
    margin: 0;
    display: none;
  }
  #filter-btn {
    min-width: 296px;
    min-height: 32px;
    width: 296px!important;
    height: 32px!important;
    margin-left: auto;
    margin-right: auto;
    margin-top: 0;
    margin-bottom: 12px;
  }
  .header__date__container {
    width: 250px!important;
    overflow: hidden;
    text-overflow: ellipsis;
    grid-template-columns: 16px 49px 1px 70px 1px 31px!important;
    height: 32px;
    text-align: center;
    padding: 3px 3px!important;
    font-size: 80%;
    margin-top: 13px;
    margin-bottom: 10px;


  }
  .header__date__container-column {
    width: 104px;
    font-size: 90%;
  }
  .header-filters {
    padding: 0;
  }
  .options__wrap {
    width: 0;
  }
  .header-search {
    justify-content: start;
  }
}
@media screen and (min-width: 321px) and (max-width: 480px) {
  #app__header {
    width: 480px;
  }
  #menu_burger {
    display: flex;
    width: 36px;
    height: 36px;

  }
  .logo__btn {
    margin-right: 16px!important;
    margin-left: 20px!important;
    width: 36px!important;
    height: 36px!important;
  }
  #logo {
    display: none;
  }
  #btn_1,
  #btn_2,
  #btn_3, #btn_4,
  #btn_5, #btn_6, #btn_7, #line_hidden,
  .header__select,
  .header-filters .vertical__line {
    display: none;

  }
  .header-filters {
    display: block;
    width: 480px;
  }
  .btn__container,
  .btn__container button{
    margin: 0;
    display: none;
  }
  #filter-btn {
    min-width: 440px;
    min-height: 32px;
    width: 440px!important;
    height: 32px!important;
    margin-left: auto;
    margin-right: auto;
  }
  .header-filters {
    gap: 0;

  }
  .header__date__container {
    width: 388px!important;
    grid-template-columns: 16px 104px 1px 82px 1px 98px!important;
    height: auto;
    text-align: center;
    padding: 3px 3px!important;
    font-size: 80%;
    margin-top: 25px;
    margin-bottom: 18px;


  }
  .header__date__container-column {
    width: 104px;
    font-size: 90%;
  }
  .header-filters {
    padding: 0;
  }
  .header-search {
    justify-content: start;
    align-items: center;
    gap: 0;
  }
  .vertical__line {
    margin-left: 16px;
    margin-right: 16px;
  }
  .logo__btn {
    margin: 22px 8.1% 15px 42px;
  }


  .header__date__container-column:first-child {
    width: 16px;
  }
  .header__date__container .vertical__line {margin: 0}

  .btn__container {
    margin-left: 1.9%;
  }
  .header__button {
    width: 148px!important;
  }
}
@media screen and (min-width: 481px) {
  #menu_burger {
    display: none;
  }
}

@media screen and (min-width: 481px) and (max-width: 1024px) {
  #btn_1,
  #btn_2,
  #btn_3, #btn_4,
  #btn_5, #btn_6, #btn_7, #line_hidden {
    display: none;

  }


  .header-filters {
    gap: 0;

  }
  .header-search {
    justify-content: start;
    gap: 0;
  }
  .vertical__line {
    margin-left: 16px;
    margin-right: 16px;
  }
  .logo__btn {
    margin: 22px 8.1% 15px 42px;
  }
  .header__date__container {
    width: 481px!important;
    grid-template-columns: 16px 119px 1px 119px 1px 119px!important;
    height: 52px;
    padding: 6px 6px!important;



  }
  .header__date__container-column {
    width: 119px;
    letter-spacing: 0.005em;
    vertical-align: middle;


  }
  .header__date__container-column:first-child {
    width: 16px;
  }
  .header__date__container .vertical__line {
    margin: 0}

  .btn__container {
    margin-left: 1.9%;
  }
  .header__button {
    width: 148px!important;
  }
}

@media screen and (min-width: 1025px) and (max-width: 1920px) {

  #btn_5, #btn_6, #btn_7{
    display: none;
  }
  .logo__btn {
    margin: 22px 18% 15px 42px;
  }
  .btn__container {
    margin-left: 1.75%;
  }
}
</style>
