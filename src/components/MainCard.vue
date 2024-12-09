<template>
    <div class="main">
        <div class="content">
            <div class="content-left">
                <p class="place-name">London</p>
                <div class="temperature">
                    <span>30&deg;</span>
                </div>
                <div class="widget-group">
                    <Widget :content="humidityPercent" :header="'Humidity'" />
                    <Widget :content="windSpeed" :header="'Wind speed'" />
                </div>
            </div>
            <div class="content-right">
                <img :src="require('@/assets/clear-moon.png')" alt="clear-moon" style="width: 90px; height :90px">
                <p style="font-weight: 700; color:white; font-size:32px">Clear</p>
            </div>
        </div>
    </div>
</template>

<script>
import Widget from './Widget.vue';

export default {
    data() {
        return {
            humidityPercent: 75,
            windSpeed: 7,
        };
    },
    components: {
        Widget
    }
}
</script>

<style scoped>
.main {
    padding: 4em;
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
</style>