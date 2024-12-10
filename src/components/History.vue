<template>
    <h1>History</h1>
    <div class="container">
        <div class="scroll-container">
            <div class="item">
                <span class="palce-name">London</span>
                <img :src="require('@/assets/clear-moon.png')" alt="clear-moon" style="width: 40px; height :40px">
                <span>Clear</span>
                <span class="temperature">30&deg;</span>
            </div>
            <div class="item">
                <span class="palce-name">London</span>
                <img :src="require('@/assets/clear-moon.png')" alt="clear-moon" style="width: 40px; height :40px">
                <span>Clear</span>
                <span class="temperature">30&deg;</span>
            </div>
            <div class="item">
                <span class="palce-name">London</span>
                <img :src="require('@/assets/clear-moon.png')" alt="clear-moon" style="width: 40px; height :40px">
                <span>Clear</span>
                <span class="temperature">30&deg;</span>
            </div>
            <div class="item">
                <span class="palce-name">London</span>
                <img :src="require('@/assets/clear-moon.png')" alt="clear-moon" style="width: 40px; height :40px">
                <span>Clear</span>
                <span class="temperature">30&deg;</span>
            </div>
            <div class="item">
                <span class="palce-name">London</span>
                <img :src="require('@/assets/clear-moon.png')" alt="clear-moon" style="width: 40px; height :40px">
                <span>Clear</span>
                <span class="temperature">30&deg;</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {

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
</style>