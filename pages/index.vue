<template>
    <div class="testing text-white">{{ parseFloat(total).toFixed(2) }}</div>
    <div class="seleccion">
        <select name="prints" class="select select-info text-white" v-model="material">
            <option default>Seleccionar</option>
            <option v-for="(item,index) in printList" :key="index" :value="item.val">{{item.item}} {{ parseFloat(item.val).toFixed(2) }}</option>
        </select>
    </div>
    <div class="cliente grid gap-4 mt-4">
        <label class="input input-info">
            <small>Width</small>
            <input type="text" v-model="valW">
        </label>
        <label class="input input-info">
            <small>Height</small>
            <input type="text" v-model="valH">
        </label>
    </div>
    <div class="calc my-6">
        <button class="btn btn-success text-white rounded-full" @click="calcula()">clc</button>
        <button class="btn btn-warning text-white rounded-full" @click="clr()">clr</button>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const printList = ref([
    {item:'Vinyl',val:12},
    {item:'VinylLaminado',val:17},
    {item:'Vinyl + Corte',val:15},
    {item:'VinylMicroperf',val:15},
    {item:'VinylMicroperf + Instal',val:22},
    {item:'VinylPlot + Transf',val:24},
    {item:'Vinyl + Instal',val:22},
    {item:'Lona',val:8},
    {item:'Lona + Instal',val:14},
    {item:'Estructura opaca',val:38},
    {item:'Totem rtaslucido',val:145},
    {item:'Estructura traslucida',val:110},
    {item:'LonaTrasl',val:12},
    {item:'DTF',val:12},
    {item:'UV A3',val:15},
    {item:'MDF 3mm corte',val:45},
    {item:'MDF 3mm corte + vinyl',val:45}
])

const total = ref(0)

const material = ref(0)

const valH = ref(0)

const valW = ref(0)

const valReq = ref(0)

const calcula = () =>{
    let alt = (valH.value * 1) / 100
    let anc = (valW.value * 1) / 100
    let test = alt * anc * material.value
    //console.log(alt)
    total.value = test
}
const clr=()=>{
    total.value = 0
    valH.value = 0
    valW.value = 0
    material.value = 0
}
</script>