<template>
    <transition name="fade" @before-enter="beforeEnter" @enter="enter" @leave="leave">
        <div v-if="weatherData" :key="weatherData.name" class="main">
            <div class="content">
                <div class="content-left">
                    <p class="place-name">{{ weatherData.name }}</p>
                    <div class="temperature">
                        <span>{{ Math.round(weatherData.main.temp) }}&deg;</span>
                    </div>
                    <div class="widget-group">
                        <Widget :content="weatherData.main.humidity" :header="'Humidity'" />
                        <Widget :content="weatherData.wind.speed" :header="'Wind speed'" />
                    </div>
                </div>
                <div class="content-right">
                    <img :src="getWeatherImage(weatherData.weather[0].main)" :alt="weatherData.weather[0].main"
                        style="width: 90px; height: 90px">
                    <p style="font-weight: 700; color:white; font-size:32px">{{ weatherData.weather[0].main }}</p>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
import Widget from './Widget.vue';

export default {
    props: {
        weatherData: {
            type: Object,
            required: false,
        },
    },
    components: {
        Widget
    },
    methods: {
        getWeatherImage(weatherCondition) {
            switch (weatherCondition) {
                case 'Clear':
                    return require('@/assets/Clear.png');
                case 'Clouds':
                    return require('@/assets/Clouds.png');
                case 'Rain':
                    return require('@/assets/Rain.png');
                case 'Thunderstorm':
                    return require('@/assets/Thunderstorm.png');
                case 'Snow':
                    return require('@/assets/Snow.png');
                case 'Fog':
                    return require('@/assets/Mist.png');
                case 'Mist':
                    return require('@/assets/Mist.png');
                default:
                    return require('@/assets/Clear.png');
            }
        },
        beforeEnter(el) {
            el.style.opacity = 0; // Start with an opacity of 0
        },
        enter(el, done) {
            el.offsetHeight; // Trigger reflow to ensure transition runs
            el.style.transition = 'opacity 1s ease'; // Define the transition
            el.style.opacity = 1; // Fade to opacity 1
            done(); // Signal that the transition is complete
        },
        leave(el, done) {
            el.style.transition = 'opacity 1s ease'; // Define the transition
            el.style.opacity = 0; // Fade out
            done(); // Signal that the transition is complete
        }
    }
}
</script>

<style scoped>
.main {
    margin: 4em;
    display: flex;
    justify-content: center;
}

.content {
    display: flex;
    justify-content: center;
    gap: 11em;
    width: 45em;
    height: 20em;
    background-color: rgba(217, 217, 217, 0.2);
    border-radius: 30px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
}

.content-left {
    color: white
}

.place-name {
    font-size: 32px;
    font-weight: 700;
    padding-right: 2em;
    padding-top: 0.5em;
}

.temperature {
    font-size: 64px;
    font-weight: 900;
    padding-left: 0.5em;
}

.widget-group {
    display: flex;
    padding-top: 2em;
    gap: 30px;
}

.content-right {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

/* Fade Transition Styles */
.fade-enter-active,
.fade-leave-active {
    transition: opacity 1s ease;
}

.fade-enter,
.fade-leave-to

/* .fade-leave-active in <2.1.8 */
    {
    opacity: 0;
}
</style>
