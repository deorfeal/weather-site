<script>

import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Main
  },
  data() {
    return {

    }
  },
}

</script>

<template>
  <Main />
</template>

<style lang="scss">
@import './assets/scss/style.scss';

.body {
  transition: background 0.3s;
}

.info-panel-view-row__temperature,
.info-panel-view-desc,
.info-panel-view-bottom__row,
.all-information-top__title,
.information-item__day,
.information-item__row,
.inf-today__title,
.inf-today-item-column-row__box-sunrise,
.inf-today-item-column-row__box-sunset,
.inf-today-item__digits,
.inf-today-item__km,
.inf-today-item__digit {
  transition: color 0.3s;
}

.info-panel {
  transition: background 0.3s, border 0.3s;
}

.inf-today-item {
  transition: background 0.3s, border 0.3s, transform 0.3s;
}

.all-information-top {
  transition: background 0.3s, border 0.3s;
}

.info-panel-form {
  transition: background 0.3s
}

.info-panel-form__input {
  transition: color 0.3s;

  &::placeholder {
    transition: color 0.3s;
  }
}

.info-panel-form__btn svg path {
  transition: fill 0.3s;
}

.info-panel-form__input svg {
  transition: fill 0.3s;
}

.information-item__img {
  transition: filter 0.3s;
}

.inf-today-item-column-row__svg {
  transition: filter 0.3s;
}

.inf-today-item__wind path {
  transition: stroke 0.3s;
}

.inf-today-item__uv {
  transition: filter 0.3s;

  g {
    path {
      transition: fill 0.3s;
    }

    path:nth-last-child(1) {
      transition: fill 0.3s;
      transition: stroke 0.3s;
    }
  }

}

.info-panel-view-bottom__row svg path {
  transition: stroke 0.3s;
}

.info-panel-view-row__img {
  transition: filter 0.3s;
}

.all-information-top-settings__btn svg path {
  transition: stroke 0.3s;
}

.all-information-top-settings__c {
  transition: background 0.3s, color 0.3s, transform 0.3s;
}

.all-information-top-settings__f {
  transition: background 0.3s, color 0.3s, transform 0.3s;
}

// // // // // // // // // // // 

.body--dark {
  #app {
    background:#121212;
    transition: background 0.3s;
  }
  .info-panel {
    background: #161616;
    border: 1px solid transparent;
    transition: background 0.3s, border 0.3s;
  }

  .inf-today-item {
    background: #161616;
    border: 1px solid transparent;
    transition: background 0.3s, border 0.3s, transform 0.3s;
  }

  .information-item {
    background: #161616;
    border: 1px solid transparent;
    transition: background 0.3s, border 0.3s, transform 0.3s;
  }

  .all-information-top {
    background: #161616;
    border: 1px solid transparent;
    transition: background 0.3s, border 0.3s;
  }

  .info-panel-form {
    background: #121212;
    transition: background 0.3s;
  }

  .info-panel-view-row__temperature,
  .info-panel-view-desc,
  .info-panel-view-bottom__row,
  .all-information-top__title,
  .information-item__day,
  .information-item__row,
  .inf-today__title,
  .inf-today-item-column-row__box-sunrise,
  .inf-today-item-column-row__box-sunset,
  .inf-today-item__digits,
  .inf-today-item__km,
  .inf-today-item__digit {
    color: #fcfcfc;
    transition: color 0.3s;
  }

  .info-panel-form__input {
    color: #fcfcfc;
    transition: color 0.3s;

    &::placeholder {
      transition: color 0.3s;
      color: #b2b2b2;
    }
  }

  .info-panel-form__btn svg path {
    fill: #fcfcfc;
    transition: fill 0.3s;
  }

  .info-panel-form__input svg {
    fill: #fcfcfc !important;
    transition: fill 0.3s;
  }

  .information-item__img {
    filter: none;
    transition: filter 0.3s;
  }

  .inf-today-item-column-row__svg {
    filter: none;
    transition: filter 0.3s;
  }

  .inf-today-item__wind path {
    stroke: #fcfcfc;
    transition: stroke 0.3s;
  }

  .inf-today-item__uv {
    filter: none;
    transition: filter 0.3s;

    g {
      path {
        fill: #fcfcfc !important;
        transition: fill 0.3s;
      }

      path:nth-last-child(1) {
        fill: none !important;
        stroke: #fcfcfc !important;
        transition: fill 0.3s, stroke 0.3s;
      }
    }

  }

  .info-panel-view-bottom__row svg path {
    stroke: #fcfcfc !important;
    transition: stroke 0.3s;
  }

  .info-panel-view-row__img {
    filter: none;
    transition: filter 0.3s;
  }

  .all-information-top-settings__btn svg path {
    stroke: #fff;
    transition: stroke 0.3s;
  }

  .all-information-top-settings__mode-moon {
    display: none;
  }

  .all-information-top-settings__mode-sun {
    display: block;
  }

  .all-information-top-settings__c  {
    background: #000;
    color: #fff;
  }

  .all-information-top-settings__f {
    background: #000;
    color: #fff;
  }

  .all-information-top-settings--active {
    background: #fff;
    color: #000;
    transition: background 0.3s, color 0.3s;
  }


}
</style>