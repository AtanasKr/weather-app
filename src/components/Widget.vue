<template>
    <div class="widget-main">
        <div class="widget-left">
            <img :src="require(header === 'Humidity' ? '@/assets/humidity-widget.png' : '@/assets/wind-widget.png')"
                alt="widget-icon" style="width: 50px; height: 50px" />
        </div>
        <div class="widget-right">
            <p class="content-holder">{{ content }}{{ header === 'Humidiry' ? '%' : 'km/h' }}</p>
            <p>{{ header }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: ['content', 'header', 'widgetFor'],
}
</script>

<style scoped>
p {
    margin: 0;
    font-weight: bold;
}

.content-holder {
    text-align: center;
}

.widget-main {
    display: flex;
    justify-content: left;
    align-items: center;
}
</style>