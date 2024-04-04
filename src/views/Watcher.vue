<script setup>
import { reactive, computed , watch} from 'vue'
const counterData = reactive({
    count: 0,
    title: "My counter"
})

const increaseCounter = amount => {
    counterData.count += amount
}

const decreaseCounter = amount => {
    counterData.count -= amount
}

const oddOreven = computed(() => {
    return counterData.count % 2 == 0 ? 'even' : 'odd';
})

watch(()=> counterData.count, (newCount) =>{
    if( newCount >= 5) {
        counterData.title = 'My counter is greater than 5!'
    }
    else if(newCount < 0){
        counterData.title = 'My counter is lower than 0!'
    }
    else{
        counterData.title = 'My counter'
    }
})

const vAutoFocus = {
    mounted : (element) => {
        element.focus()
    }
}

</script>

<template>
    <div class="watcher">
        <h1> {{ counterData.title }} </h1>
        <input type="text" v-model="counterData.title" v-autofocus>
        <button @click="decreaseCounter(2)">--</button>
        <button @click="decreaseCounter(1)">-</button>     
        <span>{{ counterData.count }}</span>
        <button @click="increaseCounter(1)">+</button>
        <button @click="increaseCounter(2)">++</button>
        <p><span> This counter is {{  oddOreven }}</span></p>
    </div>
</template>

<style>
@media (min-width: 1024px) {
    button {
        width: 5vh;
        align-items: center;
        justify-content: center;

    }

    span {
        font-size: 5vh;
        margin: 5vh;
        align-items: center;
        justify-content: center;
    }

}
</style>