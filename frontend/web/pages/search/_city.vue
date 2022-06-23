<template>
  <v-container fluid pa-0 class="search__container">
    <v-row class="search__container__row">
      <v-col>
        <v-list class="objects-container">
          <v-list-item v-for="i in 10"
                       :key="i"
                       class="">
            <object-card></object-card>
          </v-list-item>
          <v-row class="see_all">
            <v-btn
              width="210px"
              height="32px"
              color="rgba(0,172,162,1)"
              >
              <v-icon
              width="16px"
              height="16px"
              >mdi-plus</v-icon>
              Показать ещё
            </v-btn>
          </v-row>
          <v-row class="pagination">
              <v-pagination
                v-model="page"
                :length="3"
                :total-visible="3"
                circle
                color="#00ACA2"
                text-color="white"
              ></v-pagination>
          </v-row>
        </v-list>
      </v-col>

      <v-col
        cols="12"
        md="6"
        lg="7"
        xl="8"
        class="flex-column align-end search__container__row__map"
      >
        <search-map @update:bounds="updateMapBoundsHandler"></search-map>
      </v-col>
    </v-row>
  </v-container>

</template>

<script>
import { mapActions } from 'vuex'

import ObjectCard from '../../components/cards/ObjectCard'
import SearchMap from '../../components/maps/SearchMap'

export default {
  name: 'SearchPage',
  components: { SearchMap, ObjectCard },
  layout: 'search',
  data() {
    return {
        page: 1,
    }
  },
  computed: {},
  mounted() {
    this.list()
  },
  methods: {
    ...mapActions({
      list: 'web/search/getList',
      map: 'web/search/getPoints'
    }),
    updateMapBoundsHandler(bounds){
      console.log('updateMapBoundsHandler', bounds);
      this.map(bounds);
    }
  },
}
</script>

<style scoped>

.v-pagination__item {
  background: transparent!important;
  color: #37373A!important;
  box-shadow: none;
}
.pagination {
  display: flex;
  background-color: transparent;
  justify-content: center;
  width: 100%;
  padding-top: 27px;
  padding-bottom: 20px;
}

.search__container {
  height: calc(100vh - 64px);
}
.search__container__row {
  height: 100%;
  width: 100%;
}
.search__container__row__map {
  width: 1653px;
  position: fixed;
  right: 0px;
  height: 100%;
  padding: 180px 0 0 0;
}

.objects-container {
  width: 847px!important;
  padding-top: 180px;
  padding-left: 20px!important;
  padding-right: 20px!important;
  box-sizing: border-box;
  box-shadow: none;
  border: none;
  background-color: #BDBDBD;
  margin-bottom: 128px;
}
.objects-container .v-list-item {
  width: 807px;
  flex-basis: auto;
  margin-bottom: 20px;
}

.v-list-item {
  padding: 0;
}

@media screen and (max-width: 320px) {
  .search__container__row__map {
    display: none;
  }
  .objects-container {
    width: 320px!important;
    padding-top: 130px!important;
    padding-left: 0!important;
    padding-right: 0!important;
  }
  .objects-container .v-list-item {
    width: 320px;
    height: 309px;
    margin-bottom: 20px;

  }
  .see_all {
    display: flex;
    width: 100%;
    justify-content: center;
    margin-bottom: 20px;
    color: white!important;
    align-items: center;
  }

  .see_all button {
    color: white!important;
    text-transform: none;
    border-radius: 16px;
  }
  .see_all button span {
    display: flex;
    justify-content: space-between;
    width: 80%;
  }
  .see_all v-btn {
    width: 210px;
    height: 32px;
    padding: 8px 24px;
    background-color: rgba(0,172,162,1);


    box-sizing: border-box;


  }
  .pagination {
    display: none;
  }
  .objects-container .v-list-item:nth-child(7),
  .objects-container .v-list-item:nth-child(8),
  .objects-container .v-list-item:nth-child(9),
  .objects-container .v-list-item:nth-child(10) {
    display: none;
  }
}
@media screen and (min-width: 321px) and (max-width: 480px) {
  .search__container__row__map {
    display: none;
  }
  .objects-container {
    width: 480px!important;
    padding-right: 20px;
    padding-left: 20px;
  }
  .objects-container .v-list-item {
    width: 440px;
    height: 177px;
    margin-bottom: 20px;

  }

  .pagination {
    width: 480px;
  }
  .pagination .v-list {

    margin: 20px auto 26px auto;

  }
  .see_all {
    display: flex;
    width: 100%;
    justify-content: center;
    margin-bottom: 20px;
    color: white!important;
    align-items: center;
  }

  .see_all button {
    color: white!important;
    text-transform: none;
    border-radius: 16px;
  }
  .see_all button span {
    display: flex;
    justify-content: space-between;
    width: 80%;
  }
  .see_all v-btn {
    width: 210px;
    height: 32px;
    padding: 8px 24px;
    background-color: rgba(0,172,162,1);


    box-sizing: border-box;


  }
  .pagination {
    display: none;
  }
}
@media screen and (min-width: 481px) and (max-width: 1024px) {
  .see_all {
    display: none;
  }
  .search__container__row__map {
    width: 50%;
  }

  .objects-container {
    width: 50%!important;
    padding-right: 20px;
    padding-left: 20px;



  }

/*  .objects-container .v-list-item {
    width: 482px;
    height: 177px;
    margin-bottom: 20px;

  }*/
  .pagination {
    width: 522px;
  }
  .pagination .v-list {

    margin: 20px auto 26px auto;

  }

}
@media screen and (min-width: 1025px) and (max-width: 1920px) {
  .see_all {
    display: none;
  }
  .search__container__row__map {
    width: 1108px;
  }
  .objects-container {
    width: 812px;
    padding-right: 20px;
    padding-left: 20px;
  }

}
/*
по умолчанию:
@media screen and (max-width: 2500px)
*/

@media screen and (min-width: 1921px) and (min-width: 2500px) {
  .see_all {
    display: none;
  }
  .search__container__row__map {
    width: 67%;
  }
  .objects-container {
    width: 33%!important;
  }
}
</style>
