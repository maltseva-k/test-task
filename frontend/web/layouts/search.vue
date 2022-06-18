<template>
  <v-app light>
    <base-header
      search />
<!--    <full-search-form></full-search-form>-->
    <v-main app class="pa0">
      <Nuxt />
    </v-main>
    <v-footer
      padless
      fixed
    >
      <v-row>
        <ul class="footer-nav">
          <li><a>О проекте</a></li>
          <li><a>Руководство</a></li>
          <li><a>Правила</a></li>
          <li><a>Помощь</a></li>
        </ul>
      </v-row>
      <v-row class="footer-line"></v-row>
      <v-row class="footer-social">
        <a class="footer-social-btn">
          <img src="/facebook.svg">
        </a>
        <a class="footer-social-btn">
          <img src="/twitter.svg">
        </a>
        <a class="footer-social-btn">
          <img src="/telegram.svg">
        </a>
      </v-row>
      <v-row
        justify="center footer-logo"
        no-gutters
      >
          {{ new Date().getFullYear() }} © ООО “Понаехали”
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
/* import FullSearchForm from '../components/forms/search/FullSearchForm' */
import BaseHeader from './includes/BaseHeader'
export default {
  name: 'SearchLayout',
  components: { BaseHeader },
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
    }
  },
  computed: {
    isFullPage() {
      return (
        this.$route.matched.map((r) => {
          return r.components.default.options.isFullPage
        })[0] || false
      )
    },
  },
}
</script>
<style>

footer {
  background-color: #EBEBEC;
  width: 100%;
  height: 128px;
  display: flex;
  justify-content: center;
  flex-direction: column;

}
footer .row {
  margin: 0;
  flex: none;
}
.footer-logo {
  color: rgba(95, 95, 97, 1);
  margin-bottom: 3px;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
}
footer .row ul {
  padding-left: 0;
}
.footer-nav {
  max-width: 418px;
  display: flex;
  justify-content: space-between;
  padding-top: 22px;
  padding-bottom: 14px;
  padding-left: 0;
  margin-left: auto;
  margin-right: auto;

}

.footer-nav li {
  list-style: none;
  margin-right: 36px;



}

.footer-nav li:last-child {
  margin-right: 31px;
}

.footer-nav li a {
  color: rgba(95, 95, 97, 1);
  text-decoration: none;
  font-weight: 500;
  font-size: 14px;
  line-height: 28px;
  /*margin-right: 36px;*/
}

.footer-nav li a:last-child {
 /* margin-right: 31px;*/
}

.footer-social {
  display: flex;
  justify-content: space-between;
  padding-top: 8px;
  padding-bottom: 8px;
  width: 134px!important;
  margin-left: auto;
  margin-right: auto;
}

.footer-social .footer-social-btn {
  text-decoration: none;
  border-radius: 50%;
  width: 24px;
  height: 24px;
  padding: 5px;
  display: flex;
  justify-content: center;
  vertical-align: center;
  align-items: center;
  background-color: rgba(95, 95, 97, 1);
  color: white;
}

.footer-social .footer-social-btn:last-child {
  padding: 5px 6.8px 5px 5px;
}


footer .row + .row {
  margin: 0;
}

.footer-line {
  height: 1px;
  width: 1180px;
  margin-left: auto;
  margin-right: auto;
  background-color: rgba(95, 95, 97, 1);

}

.footer-logo {
  width: 171px;
  height: 20px;
  text-align: center;
  margin-left: auto;
  margin-right: auto;
}

@media screen and (max-width: 320px) {
  footer {
    align-items: start!important;
  }
  .footer-nav li {
    list-style: none;
    margin-right: auto;
    margin-left: 0;
  }

  .footer-line {
    height: 1px;
    width: 250px;
  }
  .footer-nav {
    max-width: 320px;
    display: flex;
    justify-content: start;
    flex-direction: column;
    padding: 0;
    margin: 0 auto 0 0;
  }
  footer {
    width: 320px;
    height: 204px;
    display: flex;
    justify-content: start;
    flex-direction: column;
    padding: 12px 20px;

  }
  .footer-social {
    margin: 0;
    width: 100% !important;
    justify-content: start!important;
  }
  .footer-logo {
    width: 320px;
    text-align: start!important;
    justify-content: start;
    margin: 0 auto 0 0;
  }
}
@media screen and (min-width: 331px) and (max-width: 480px) {
  .footer-line {
    height: 1px;
    width: 300px;
  }
}
@media screen and (max-width: 1024px) {

}
@media screen and (max-width: 1920px) {


}
/*
по умолчанию:
@media screen and (max-width: 2500px)
*/
</style>
