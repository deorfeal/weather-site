<template>
    <div class="info-panel">
        <form class="info-panel__form info-panel-form" action="#">
            <button class="info-panel-form__btn" type="button">
                <svg width="15px" height="15px" viewBox="0 0 27 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path fill-rule="evenodd" clip-rule="evenodd"
                        d="M21.9996 11.6472C21.9996 16.9753 17.6807 21.2943 12.3536 21.2943C7.02638 21.2943 2.70752 16.9753 2.70752 11.6472C2.70752 6.319 7.02638 2 12.3536 2C17.6807 2 21.9996 6.319 21.9996 11.6472ZM17.8076 21.9407C16.1806 22.8048 14.3242 23.2943 12.3536 23.2943C5.92163 23.2943 0.70752 18.0797 0.70752 11.6472C0.70752 5.21461 5.92163 0 12.3536 0C18.7855 0 23.9996 5.21461 23.9996 11.6472C23.9996 15.3899 22.2344 18.7203 19.4912 20.8511L26.5258 30.1465L24.931 31.3534L17.8076 21.9407Z"
                        fill="#000" fill-opacity="1" />
                </svg>
            </button>
            <input disabled="disabled" class="info-panel-form__input" placeholder="New York" type="text">
            <svg fill="#b2b2b2" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink" width="15px" height="15px" viewBox="0 0 395.71 395.71"
                xml:space="preserve">
                <g>
                    <path d="M197.849,0C122.131,0,60.531,61.609,60.531,137.329c0,72.887,124.591,243.177,129.896,250.388l4.951,6.738
                    c0.579,0.792,1.501,1.255,2.471,1.255c0.985,0,1.901-0.463,2.486-1.255l4.948-6.738c5.308-7.211,129.896-177.501,129.896-250.388
                    C335.179,61.609,273.569,0,197.849,0z M197.849,88.138c27.13,0,49.191,22.062,49.191,49.191c0,27.115-22.062,49.191-49.191,49.191
                    c-27.114,0-49.191-22.076-49.191-49.191C148.658,110.2,170.734,88.138,197.849,88.138z" />
                </g>
            </svg>
        </form>
        <div class="info-panel__view info-panel-view">
            <div class="info-panel-view__row info-panel-view-row">
                <img class="info-panel-view-row__img" :src="this.iconsWay + this.weatherDataInf.icon + '.svg'"
                    alt="icon">
                <div class="info-panel-view-row__temperature">
                    <span class="info-panel-view-row__temperature-text">{{ this.dataOfTemp.value }}</span>
                    <span class="info-panel-view-row__temperature-system">{{ this.dataOfTemp.system }}</span>
                </div>
            </div>
            <div class="info-panel-view__desc info-panel-view-desc">
                <p class="info-panel-view-desc__place">
                    {{ this.weatherRawInf.address }}
                </p>
                <p class="info-panel-view-desc__date">
                    <span class="info-panel-view-desc__date-day">
                        {{ this.listOfDays[this.currentDay] }},
                    </span>
                    <span class="info-panel-view-desc__date-mounth">
                        {{ this.listOfMounths[this.currendMounth] }},
                    </span>
                    <span class="info-panel-view-desc__date-digit">
                        {{ this.currentDate }}
                    </span>
                </p>
            </div>
            <div class="info-panel-view__bottom info-panel-view-bottom">
                <div class="info-panel-view-bottom__row">
                    <svg width="20px" height="20px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M7.27004 13.01C6.74004 12.74 6.15004 12.6 5.55004 12.6C0.870039 12.93 0.870039 19.74 5.55004 20.07H16.64C17.99 20.08 19.29 19.58 20.28 18.67C23.57 15.8 21.81 10.03 17.48 9.48C15.92 0.110001 2.39004 3.67 5.60004 12.6"
                            stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round"
                            stroke-linejoin="round" />
                        <path d="M15.8501 9.92001C16.3701 9.66001 16.9401 9.52001 17.5201 9.51001" stroke="#292D32"
                            stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                    <div class="info-panel-view-bottom__row-desc">
                        {{ this.weatherDataInf.conditions }}
                    </div>
                </div>
                <div class="info-panel-view-bottom__row">
                    <svg width="20px" height="20px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M16 14L12 12V7M12 21C16.9706 21 21 16.9706 21 12C21 7.02944 16.9706 3 12 3C7.02944 3 3 7.02944 3 12C3 16.9706 7.02944 21 12 21Z"
                            stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                    <div class="info-panel-view-bottom__row-time">
                        {{ currentTimeString }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>

export default {
    name: 'InfoPanel',
    props: ['weatherDataInf', 'weatherDaysInf', 'weatherRawInf'],
    inject: ['fahrenheits'],
    data() {
        return {
            currentDay: '',
            listOfDays: [
                'Sunday',
                'Monday',
                'Tuesday',
                'Wednesday',
                'Thursday',
                'Friday',
                'Saturday'
            ],
            currendMounth: '',
            listOfMounths: [
                'January',
                'February',
                'March',
                'April',
                'May',
                'June',
                'July',
                'August',
                'September',
                'October',
                'November',
                'December',
            ],
            currentDate: '',
            iconsWay: '../src/assets/images/icons/weather/',
            dataOfTemp: { value: Math.floor(this.weatherDataInf.temp), system: '°C' },
        }
    },
    mounted() {
        let daysTime = this.weatherDataInf.datetimeEpoch
        let daysTimeCurrentString = daysTime.toString() + '000'
        let daysTimeNumber = +daysTimeCurrentString
        let daysTimeResult = new Date(daysTimeNumber)
        this.currentDay = daysTimeResult.getDay()
        this.currendMounth = daysTimeResult.getMonth()
        this.currentDate = daysTimeResult.getDate()
    },
    computed: {
        currentTimeString() {
            return String(this.weatherDataInf.datetime).slice(0, 5)
        }
    },
    watch: {
        fahrenheits: {
            handler() {
                if( this.fahrenheits.value == true ) {
                    this.dataOfTemp.value =  Math.floor(this.weatherDataInf.temp * 1.8 + 32)
                    this.dataOfTemp.system = '°F'
                } else {
                    this.dataOfTemp.value = Math.floor(this.weatherDataInf.temp)
                    this.dataOfTemp.system = '°C' 
                }
            },
            deep: true
        },
    }
}
</script>

<style lang="scss">
@import '../assets/scss/vars';

.info-panel {
    border: 1px solid #f1f1f1;
    width: 400px;
    min-width: 400px;
    max-width: 400px;
    border-radius: 0 0px 20px 0;
    background: #fff;
    box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.25);

    @include adaptiv-value("padding-top", 20, 10, 1);
    @include adaptiv-value("padding-bottom", 20, 0, 1);
    @include adaptiv-value("padding-right", 40, 20, 1);
    @include adaptiv-value("padding-left", 40, 20, 1);
}

.info-panel-form {
    background: #f1f1f1;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px;
    border-radius: 9999px;
    position: relative;
    @include adaptiv-value("height", 40, 30, 1);

    &__btn {
        display: none;
        @include adaptiv-value("width", 15, 13, 1);
        @include adaptiv-value("height", 15, 13, 1);
        position: absolute;
        top: 50%;
        left: 10px;
        transform: translateY(-50%);

        svg {
            @include adaptiv-value("width", 15, 13, 1);
            @include adaptiv-value("height", 15, 13, 1);
        }
    }

    &__input {
        width: 100%;
        background: transparent;
        padding-right: 25px;
        @include adaptiv-value("padding-left", 10, 5, 1);
        @include adaptiv-value("font-size", 14, 12, 1);

        &::placeholder {
            @include adaptiv-value("font-size", 16, 14, 1);
        }
    }

    svg:nth-child(3) {
        position: absolute;
        top: 50%;
        right: 10px;
        transform: translateY(-50%);
        @include adaptiv-value("width", 15, 13, 1);
        @include adaptiv-value("height", 15, 13, 1);
    }
}

.info-panel-view {
    padding: 30px 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    @include adaptiv-value("padding-top", 30, 15, 1);
    @include adaptiv-value("padding-bottom", 30, 20, 1);
    @include adaptiv-value("padding-right", 20, 15, 1);
    @include adaptiv-value("padding-left", 20, 15, 1);
}

.info-panel-view-row {
    &__img {
        @include adaptiv-value("width", 150, 75, 1);
        @include adaptiv-value("height", 150, 80, 1);
        @include adaptiv-value("margin-left", -11, -1, 1);
        filter: invert(1);
    }

    &__temperature {
        @include adaptiv-value("font-size", 60, 30, 1);
        @include adaptiv-value("line-height", 70, 36, 1);
        font-weight: 300;
        margin-bottom: 20px;
        margin-top: 30px;
    }

    &__temperature-text {}

    &__temperature-system {
        vertical-align: super;
    }
}

.info-panel-view-desc {
    display: flex;
    justify-content: space-between;
    padding-bottom: 10px;
    align-items: flex-end;
    border-bottom: 2px solid #f1f1f1;
    @include adaptiv-value("margin-bottom", 5, 0, 1);
    @include adaptiv-value("gap", 20, 5, 1);

    &__place {
        font-weight: 500;
        @include adaptiv-value("font-size", 18, 14, 1);
        @include adaptiv-value("line-height", 22, 18, 1);
    }

    &__date {
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 16, 14, 1);
    }

    &__date-day {
        font-weight: 500;
    }

    &__date-mounth {}

    &__date-digit {}
}

.info-panel-view-bottom {
    display: flex;
    flex-direction: column;
    gap: 10px;

    &__row {
        display: flex;
        gap: 5px;
        align-items: center;

        svg {
            @include adaptiv-value("width", 20, 15, 1);
            @include adaptiv-value("height", 20, 15, 1);
        }

    }

    &__row-desc {
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 15, 14, 1);
    }

    &__row-time {
        @include adaptiv-value("font-size", 14, 12, 1);
        @include adaptiv-value("line-height", 15, 14, 1);
    }

}

@media (max-width: 1200px) {
    .info-panel {
        grid-template-columns: 1fr 1fr;
        @include adaptiv-value("padding-top", 20, 15, 1);
        @include adaptiv-value("padding-bottom", 20, 0, 1);
        @include adaptiv-value("padding-right", 40, 10, 1);
        @include adaptiv-value("padding-left", 40, 10, 1);
        min-width: 320px;
        width: unset;
    }
}

@media (max-width: 900px) {
    .info-panel-view-desc {
        flex-direction: column;
        align-items: flex-start;
    }

    .info-panel {
        min-width: 300px;
    }
}

@media (max-width: 800px) {
    .info-panel {
        box-shadow: unset;
        max-width: unset;
        border-radius: 0;
    }

    .info-panel-view-row__temperature {
        margin-top: unset;
        margin-bottom: unset;
    }

    .info-panel-view-row {
        align-items: center;
    }

    .info-panel {
        padding-left: 10px;
        padding-right: 10px;
    }
}
</style>>
