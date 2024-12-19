<template>
    <div class="main">
        <div class="upper-bg">
            <div class="inner-bg">
                <input v-model="location" type="text" placeholder="Enter your location..." @keyup.enter="fetchWeather">
                <img class="active-btn" :src="require('@/assets/search-btn.png')" alt="search-btn"
                    style="width: 40px; height :40px" @click="fetchWeather">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            location: 'London',
            apiKey: process.env.VUE_APP_WEATHER_API_KEY
        };
    },
    methods: {
        async fetchWeather() {
            if (!this.location) {
                alert('Please enter a location');
                return;
            }

            const url = `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&units=metric&appid=${this.apiKey}`;

            try {
                const response = await fetch(url);
                const data = await response.json();

                if (data.cod === 200) {
                    this.$emit('weatherFetched', data);
                } else {
                    alert('Location not found');
                    this.weatherData = null;
                }
            } catch (error) {
                console.error('Error fetching weather data:', error);
                alert('Error fetching weather data');
            }
        },
    },
    mounted() {
        if (this.location) {
            this.fetchWeather();
        }
    }
};
</script>

<style scoped>
.main {
    margin-top: 3em;
    display: flex;
    justify-content: center;
}

.upper-bg {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 40em;
    height: 5em;
    background-color: rgba(217, 217, 217, 0.2);
    border-radius: 20px;
    border: 2px solid white;
}

.inner-bg {
    display: flex;
    justify-content: left;
    align-items: center;
    padding-left: 10px;
    border: 2px solid white;
    width: 35em;
    height: 3em;
    border-radius: 15px;
}

input {
    all: unset;
    color: white;
}

input::placeholder {
    color: white;
}

.btn-group {
    margin-left: 15em;
}

.active-btn {
    cursor: pointer;
    margin-left: 18em;
}
</style>