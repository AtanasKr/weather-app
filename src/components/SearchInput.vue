<template>
    <div class="main">
        <div class="upper-bg">
            <div class="inner-bg">
                <input type="text" placeholder="Enter your location...">
                <div class="btn-group">
                    <img :src="require('@/assets/search-btn.png')" alt="search-btn" style="width: 40px; height :40px">
                    <img :src="require('@/assets/plus-btn.png')" alt="plus-btn" style="width: 40px; height :40px">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
.main {
    padding-top: 5em;
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
    padding-left: 15em
}
</style>