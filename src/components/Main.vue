<template>
    <div class="main__wrapper main-wrapper">
        <InfoPanel v-if="this.dataIsAct" :weatherDataInf="this.weatherDataNow" :weatherDaysInf="this.weatherDaysData"
            :weatherRawInf="this.weatherRawData" />
        <AllInformation @getСelsiuses="celsiusesToTrue" @getFahrenheits="fahrenheitsToTrue"
            @doDarkMode="doDarkModeEverything" v-if="this.dataIsAct" :weatherDataInf="this.weatherDataNow"
            :weatherDaysInf="this.weatherDaysData" :weatherRawInf="this.weatherRawData" />
        <Transition>
            <Teleport to="body">
                <div class="loading-block" v-if="this.dataIsAct != true">
                    <svg class="loading-block__img" width="24" height="24" viewBox="0 0 24 24" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M15.0089 17H18C20.2091 17 22 15.2091 22 13C22 11.1238 20.7083 9.54938 18.9657 9.11736C18.9884 8.9147 19 8.70871 19 8.5C19 5.46243 16.5376 3 13.5 3C10.9806 3 8.85678 4.69403 8.20557 7.00519C8.13748 7.00174 8.06894 7 8 7C5.79086 7 4 8.79086 4 11C4 11.0568 4.00118 11.1133 4.00352 11.1695C2.83649 11.5803 2 12.6925 2 14C2 15.6569 3.34315 17 5 17H7.84825L12.1318 9.50386C12.6405 8.61351 14 8.97454 14 10V14H15C15.7678 14 16.2492 14.8295 15.8682 15.4961L15.0089 17Z"
                            fill="white" />
                        <path class="loading-block__img-thunder" d="M9 17L13 10V15H15L11 22V17H9Z" fill="white" />
                    </svg>
                </div>
            </Teleport>
        </Transition>
    </div>
</template>

<script>

import InfoPanel from '../components/InfoPanel.vue'
import AllInformation from '../components/AllInformation.vue'

export default {
    name: 'Main',
    components: {
        InfoPanel,
        AllInformation,
    },
    data() {
        return {
            weatherRawData: '',
            weatherDataNow: '',
            weatherDaysData: '',
            dataIsAct: false,
            fahrenheits: {value: false},
            celsiuses: {value: true},
        }
    },
    mounted() {
        fetch("https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/New%20York?unitGroup=metric&include=events%2Ccurrent%2Cdays%2Calerts%2Chours&key=H9XN6DV2V3UJ6LUSKQGM5C22S&contentType=json", {
            "method": "GET",
            "headers": {
            }
        })
            .then(result => {
                return result.json()
            })
            .then(result => {

                this.weatherRawData = result
                this.weatherDataNow = result.currentConditions
                this.weatherDaysData = result.days.splice(0, 6)

                // console.log(result)
                // console.log(this.weatherDaysData)
                // console.log(this.weatherDataNow);
            })
            .catch(err => {
                console.error(err);
            });
    },
    watch: {
        weatherRawData: {
            handler() {
                setTimeout(() => {
                    this.dataIsAct = true
                }, 1000)
            },
            deep: true
        }
    },
    methods: {
        doDarkModeEverything() {
            let bodyEl = document.querySelectorAll('.body')
            if (bodyEl[0].classList.contains('body--dark')) {
                bodyEl[0].classList.remove('body--dark')
            } else {
                bodyEl[0].classList.add('body--dark')
            }
        },
        fahrenheitsToTrue() {
            this.celsiuses.value = false
            this.fahrenheits.value = true
        },
        celsiusesToTrue() {
            this.fahrenheits.value = false
            this.celsiuses.value = true
        }
    },
    provide() {
        return {
            fahrenheits: this.fahrenheits,
            celsiuses: this.fahrenheits
        }
    }
}
</script>

<style lang="scss">
@import '../assets/scss/vars';

.main-wrapper {
    display: flex;
    max-width: 1500px;
    margin-left: auto;
    margin-right: auto;
    position: relative;
}

.loading-block {
    position: absolute;
    top: 50%;
    bottom: 0;
    flex-direction: column;
    left: 50%;
    right: 0;
    width: 100%;
    gap: 30px;
    height: 100%;
    background: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.25);
    transform: translateX(-50%) translateY(-50%);
    border-radius: 20px;

    &__img {
        width: 30%;
        height: 30%;

        path {
            fill: #000;
        }
    }

    &__img-thunder {
        animation-name: thunder;
        animation-duration: 1s;
    }
}

@keyframes thunder {
    0% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(5%);
    }

    100% {
        transform: translateY(0);
    }
}

.v-enter-active,
.v-leave-active {
    transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
}

@media (max-width: 800px) {
    .main-wrapper {
        flex-direction: column;
    }
}
</style>>
