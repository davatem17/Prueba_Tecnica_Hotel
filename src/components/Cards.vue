<template>
    <div class="container">
        <div v-for="item in hotels" class="card">
            <h3>{{ item.name }}</h3>
            <p>Contenido de la tarjeta 1</p>
            <div class="rating">
                <div v-for="item in item.stars">
                    <input type="radio" id="star5" name="rating" value="1" checked>
                    <label for="star5"></label>
                </div>
            </div>

        </div>

    </div>
</template>

<script setup>
import { hotels } from '../data'
</script>

<style scoped>
.container {
    display: flex;
    justify-content: space-between;
}

.card {
    flex-basis: 30%;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 10px;
    background-color: #f9f9f9;
}

.rating {
    display: flex;
    justify-content: center;
}

.rating input {
    display: none;
}

.rating label {
    font-size: 30px;
    color: gold;

}

.rating label:before {
    content: '\2605';
}
</style>