<template>
  <div>
    <div @click="showLanguages = !showLanguages" class="menu-item pointer">
      <img class="langs-icon" :src="require('../assets/langs/language_icon.png')" alt="langs" />
      <span class="arrow"></span>
    </div>
    <div class="popup-langs-container" v-if="showLanguages">
        <div :class="localeLang === locale ? 'active each-lang-container pointer' : 'each-lang-container pointer'" v-for="locale in locales" :key="locale" @click="switchLocale(locale)">
          <img :src="require(`../assets/langs/${locale}.jpg`)" class="lang-image" :alt="locale" />
          <span>
            {{ languageNames[localeLang][locale] }}
          </span>
          <img class="check" v-if="localeLang === locale" :src="require('../assets/check.png')" alt="check" />
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LocaleSwitcher',
  data () {
    return {
      locales: process.env.VUE_APP_I18N_SUPPORTED_LOCALE.split(','),
      showLanguages: false,
      languageNames: {
        en: {
          en: 'English',
          si: 'Slovenian',
          srb: 'Serbian'
        },
        si: {
          en: 'Angleščina',
          si: 'Slovenščina',
          srb: 'Srbščina'
        },
        srb: {
          en: 'Engleski',
          si: 'Slovenački',
          srb: 'Srpski'
        }
      }
    }
  },
  computed: {
    localeLang: function () {
      return this.$i18n.locale
    }
  },
  methods: {
    switchLocale (locale) {
      if (this.$i18n.locale !== locale) {
        this.$i18n.locale = locale
        localStorage.setItem('lang', locale)
        this.showLanguages = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../styles/_variables.scss';

.popup-langs-container {
  position: absolute;
  right: 0;
  border: 1px solid black;
  background-color: lighten( $dark-color, 70% ) !important;
  color: lighten( $dark-color, 30% );
}
.each-lang-container {
  list-style-type: none;
  display: flex;
  align-items: center;
  padding: 10px 20px;
  min-width: 300px;
  transition: 0.1s;
  .lang-image {
    margin-right: 15px;
    border: 2px solid lighten( $dark-color, 30% );
    width: 30px;
    height: 30px;
    border-radius: 15px;
    transition: 0.1s;
    filter: grayscale(30%);
  }
}
.each-lang-container:hover {
  transition: 0.2s;
  background-color: lighten( $primary-color, 30% );
  color: lighten( $primary-color, 55% );
  .lang-image {
    border-color: lighten( $primary-color, 55% );
    filter: grayscale(0%);
  }
}
.check {
  position: absolute;
  right: 15px;
  width: 20px;
  height: 20px;
}
.active {
  background-color: lighten( $dark-color, 65% );
}
.menu-item {
  display: flex;
  align-items: center;
}
.langs-icon {
  width: 30px;
  height: 30px;
}
.arrow {
  width: 10px;
  height: 10px;
  margin-left: 10px;
  transform: rotate(-45deg) translateY(-50%);
  clip-path: polygon(0 100%, 0 0, 100% 100%);
  background-color: $lilac-color;
}
</style>
