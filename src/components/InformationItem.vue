<template>
    <div class="all-information-items__item information-item">
        <div class="information-item__day">
            {{ this.listOfDays[this.currentDay] }}
        </div>
        <img class="information-item__img" :src="this.iconsWay + this.daysData.icon + '.svg'" alt="icon">
        <div class="information-item__row">
            <p class="information-item__row-max">
                <span>{{ this.dataOfTemp.valueMax }}</span>
                <span>°</span>
            </p>
            <p class="information-item__row-min">
                <span>{{ this.dataOfTemp.valueMin }}</span>
                <span>°</span>
            </p>
        </div>
    </div>
</template>

<script>

export default {
    name: 'InformationItem',
    props: ['daysData'],
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
            iconsWay: '../src/assets/images/icons/weather/',
            dataOfTemp: { valueMax:  Math.floor(this.daysData.tempmax), valueMin:  Math.floor(this.daysData.tempmin) },
        }
    },
    mounted() {
        let daysTime = this.daysData.datetimeEpoch
        let daysTimeCurrentString = daysTime.toString() + '000'
        let daysTimeNumber = +daysTimeCurrentString
        let daysTimeResult = new Date(daysTimeNumber)
        this.currentDay = daysTimeResult.getDay()
    },
    watch: {
        fahrenheits: {
            handler() {
                if (this.fahrenheits.value == true) {
                    this.dataOfTemp.valueMax = Math.floor(this.daysData.tempmax * 1.8 + 32)
                    this.dataOfTemp.valueMin = Math.floor(this.daysData.tempmin * 1.8 + 32)
                } else {
                    this.dataOfTemp.valueMax = Math.floor(this.daysData.tempmax)
                    this.dataOfTemp.valueMin = Math.floor(this.daysData.tempmin)
                }
            },
            deep: true
        },
    }
}
</script>

<style lang="scss">
@import '../assets/scss/vars';

.information-item {
    border: 1px solid #f1f1f1;
    background: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
    @include adaptiv-value("padding-top", 25, 10, 1);
    @include adaptiv-value("padding-bottom", 25, 10, 1);
    @include adaptiv-value("padding-right", 20, 10, 1);
    @include adaptiv-value("padding-left", 20, 10, 1);
    border-radius: 10px;
    // box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.25); 
    cursor: pointer;
    max-width: 150px;
    transition: background 0.3s, border 0.3s, transform 0.3s;

    &:hover {
        transform: translateY(5%);
    }

    &__img {
        filter: invert(1);
        @include adaptiv-value("width", 65, 35, 1);
        @include adaptiv-value("height", 65, 35, 1);
    }

    &__day {
        @include adaptiv-value("font-size", 16, 12, 1);
        @include adaptiv-value("line-height", 18, 14, 1);
    }

    &__row {
        display: flex;
        gap: 5px;
        align-items: flex-end;
    }

    &__row-max {
        font-weight: 500;
        @include adaptiv-value("font-size", 16, 12, 1);
        @include adaptiv-value("line-height", 18, 14, 1);
    }

    &__row-min {
        color: #a5a5a5;
        @include adaptiv-value("font-size", 14, 10, 1);
        @include adaptiv-value("line-height", 16, 14, 1);
    }
}
</style>>
