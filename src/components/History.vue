<template v-if="searchHistory.length > 1">
    <h1>History</h1>
    <div class="container">
        <div class="scroll-container">
            <div v-for="(item, index) in searchHistory" :key="index" class="item">
                <span class="place-name">{{ item.name }}</span>
                <img :src="getWeatherImage(item.weather[0].main)" alt="Weather Icon" style="width: 40px; height: 40px">
                <span>{{ item.weather[0].main }}</span>
                <span class="temperature">{{ Math.round(item.main.temp) }}&deg;</span>
                <button @click="removeItem(index)" class="remove-btn">X</button> <!-- Remove button -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        searchHistory: {
            type: Array,
            required: false,
        },
    },
    emits: ['remove-item'],
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
        removeItem(index) {
            this.$emit('remove-item', index);
        }
    }
}
</script>

<style scoped>
h1 {
    text-align: center;
    color: white;
}

.container {
    display: flex;
    justify-content: center;
}

.scroll-container {
    display: flex;
    justify-content: center;
    overflow-x: auto;
    width: 80%;
    max-width: 100%;
}

.item {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 200px;
    height: 200px;
    margin-right: 10px;
    background-color: #d9d9d936;
    color: white;
    text-align: center;
    font-size: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin-bottom: 1em;
    position: relative;
}

span {
    padding-top: 0.5em;
    padding-bottom: 0.5em;
}

.palce-name {
    padding-top: 1em;
}

.palce-name,
.temperature {
    font-weight: 700;
}

.remove-btn {
    position: absolute;
    top: 5px;
    right: 5px;
    background-color: rgba(255, 0, 0, 0.329);
    color: white;
    border: none;
    border-radius: 50%;
    width: 25px;
    height: 25px;
    font-size: 16px;
    cursor: pointer;
}

.remove-btn:hover {
    background-color: darkred;
}
</style>
