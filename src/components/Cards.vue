<template>
    <div class="container">
        <div v-for="item in hotels" class="card">
            <h3>{{ item.name }}</h3>
            <img :src="imagen(item.name)" />
            <div class="textCard">
                <p><b>Regular</b></p>
                <p>Lunes-Viernes: {{ item.weekRegular }}$</p>
                <p>Sabado-Domingo: {{ item.weekendRegular }}$</p>
                <p>Recompensa a clientes</p>
                <p>Lunes-Viernes: {{ item.weekRewards }}$</p>
                <p>Sabado-Domingo: {{ item.weekendRewards }}$</p>
            </div>
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


const imagen = ((name) => {
    return `${name}1.jpg`
})
</script>

<style scoped>
h3 {
    text-align: center;
    margin: 0 auto;
}

.textCard{
    text-align: center;
}

img {
    align-content: center;
    width: 280px;
    height: 200px;
    display: block;
    margin-left: auto;
    margin-right: auto;
}

.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

.card {
    margin: auto;
    width: fit-content;
    margin-top: 10px;
    margin-bottom: 10px;
    flex-basis: 30%;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 10px 10px;
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