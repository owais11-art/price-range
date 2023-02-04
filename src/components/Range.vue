<script setup>
    import { computed } from 'vue';
    const props = defineProps(['price'])
    const emit = defineEmits(['updatePrice'])
    const fillWidth = computed(() => `${props.price}%`)
    const handleInput = event => emit('updatePrice', event.target.value)
</script>

<template>
    <div class="range">
        <div class="progress">
            <div class="fill"></div>
        </div>
        <input 
            type="range" 
            min="0" 
            max="100" 
            :value="price" 
            @input="handleInput"
            >
    </div>
</template>

<style scoped lang="less">
    .thumb(){
        -webkit-appearance: none;
        appearance: none;
        width: 40px;
        height: 40px;
        background: #EA346F;
        cursor: pointer;
        border-radius: 50%;
        outline: 15px solid rgba(234, 52, 111, .2);
    }
    .range{
        text-align: center;
        display: grid;
        place-items: center;
        position: relative;
        .progress{
            position: absolute;
            width: 100%;
            left: 0;
            height: 14px;
            border-radius: 10px;
            background: #4D4C53;
            z-index: 1;
            .fill{
                width: v-bind('fillWidth');
                height: 14px;
                border-radius: 10px;
                background-color: #EA346F;
            }
        }
        input{
            -webkit-appearance: none;
            appearance: none;
            border-radius: 10px;
            width: 100%;
            height: 14px;
            background: transparent;
            // background: #4D4C53;
            outline: none;
            margin: 70px 0;
            position: relative;
            z-index: 2;
            cursor: pointer;
            &::-webkit-slider-thumb{
                .thumb();
            }
            &::-moz-range-thumb{
                .thumb();
                border: none; /* firefox needs this */
            }
            &::-moz-range-progress{
                background: #EA346F;
                border-top-left-radius: 10px;
                border-bottom-left-radius: 10px;
                height: 14px;
            }
            &::-ms-fill-lower { 
                background: dodgerblue;
            }
        }
    }
</style>