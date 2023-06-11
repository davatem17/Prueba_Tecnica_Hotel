<script setup>
import { DatePicker } from 'v-calendar'
import { ref, reactive } from 'vue';
import { hotels } from '../data'
import 'v-calendar/dist/style.css'


const probar = ref ([])

const imagen =((name) => {
    return `${name}1.jpg`
})
const date = ref(new Date())
const customerType = ref("regular")


date.value.setDate(Number(date.value.getDate()))
const range = reactive({
    start: new Date(),
    end: date.value,
})

const send = (dateStart, dateEnd, customer) => {
    probar.value = []
    const date1 = new Date(invert(dateStart))
    const date2 = new Date(invert(dateEnd))
    const numberDays = countDays(date1, date2)

    const diasEntreFechas = obtenerDiasEntreFechas(date1, date2);
    if (diasEntreFechas.length > 1) {
        diasEntreFechas.push(date2)
    }
    reservationDays(diasEntreFechas, customer)
    
    // const fechaActual = weekendDay(diasEntreFechas[1])
    // console.log(diasEntreFechas)
    // console.log(fechaActual)

}

const reservationDays = (day, customer) => {
    let numberWeekDay = 0
    let numberWeekendDay = 0
    let pay = []
    let position = []
    let minimoPay = []
    

    if (day.length == 1) {
        if (weekendDay2(day[0])) {
            numberWeekendDay = numberWeekendDay + 1
        } else {
            numberWeekDay = numberWeekDay + 1
        }
    }
    for (let i = 1; i < day.length; i++) {
        if (weekendDay(day[i])) {
            numberWeekendDay = numberWeekendDay + 1
        } else {
            numberWeekDay = numberWeekDay + 1
        }
    }

    for (let i = 0; i < 3; i++) {
        if (customer == 'regular') {
            pay.push(numberWeekDay * hotels[i].weekRegular + numberWeekendDay * hotels[i].weekendRegular)
            probar.value.push({name: hotels[i].name, pago: numberWeekDay * hotels[i].weekRegular + numberWeekendDay * hotels[i].weekendRegular})
        } else {
            pay.push(numberWeekDay * hotels[i].weekRewards + numberWeekendDay * hotels[i].weekendRewards)
            probar.value.push({name: hotels[i].name, pago: numberWeekDay * hotels[i].weekRewards + numberWeekendDay * hotels[i].weekendRewards})
        }
    }
    minimoPay = pay.sort((a, b) => a - b)
    probar.value.sort((x,y)=>x.pago - y.pago)
}



const obtenerDiasEntreFechas = (dateI, dateF) => {
    const dias = []; 
    const fechaInicioSinHora = new Date(dateI.getFullYear(), dateI.getMonth(), dateI.getDate());
    const fechaFinSinHora = new Date(dateF.getFullYear(), dateF.getMonth(), dateF.getDate());
    for (let fecha = fechaInicioSinHora; fecha <= fechaFinSinHora; fecha.setDate(fecha.getDate() + 1)) {
        dias.push(new Date(fecha)); 
    }
    return dias;
}

const weekendDay = (fecha) => {
    const dia = fecha.getDay(); 
    return dia === 0 || dia === 6; 
}

const weekendDay2 = (fecha) => {
    const dia = fecha.getDay(); 
    return dia === 5 || dia === 6; 
}

const invert = (date) => {
    const partes = date.split('/');
    const invertedDate = `${partes[2]}-${partes[1]}-${partes[0]}`;
    return invertedDate
}

const countDays = (star, end) => {
    const millisecondsDay = 24 * 60 * 60 * 1000
    const differenceDates = Math.abs(end - star)
    return Math.floor(differenceDates / millisecondsDay)
}
</script>
<template>
    <div>
        <DatePicker v-model="range" is-range>
            <template v-slot="{ inputValue, inputEvents }">
                <input type="text" v-model="inputValue.start" v-on="inputEvents.start" /><br/>
                <input type="text" v-model="inputValue.end" v-on="inputEvents.end" /><br/>
                <select v-model="customerType">
                    <option value="regular">Regular</option>
                    <option value="recompensa">Recompensa al Cliente</option>
                </select>
                <button @click="send(inputValue.start, inputValue.end, customerType)">Calcular</button>
            </template>
        </DatePicker>
    </div>
    <br/>
    <div v-if="probar.length>0" class="container">
        <div v-for="item in probar" class="card">
            <h3>{{ item.name }}</h3>
            <p>Precio: {{ item.pago }}$</p>
        </div>

    </div>
</template>

<style scoped>
img{
    width: 200px;
    height: 200px;
}
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


</style>