<script setup>
    import { ref } from 'vue';
    import Range from './Range.vue'
    const price = ref(0)
    const updatePrice = amount => price.value = amount
</script>

<template>
    <main>
        <div class="price">
            <p><sup>$</sup>{{ price }}.00</p>
        </div>
        <Range
            :price="price"
            @updatePrice="updatePrice"
        />
        <div class="buy-now-btn">
            <button>buy now</button>
        </div>
    </main>
</template>

<style scoped lang="less">
    main{
        width: 500px;
        background-color: #262529;
        border-radius: 6px;
        box-shadow: 0px 0px 250px #000000;
        padding: 40px 30px;
        display: flex;
        flex-direction: column;
        gap: 20px;
        @media(max-width: 500px){
            width: 100%;
        }
        .price{
            p{
                color: #FFC700;
                text-align: center;
                font-weight: 700;
                font-size: 6rem;
                @media(max-width: 500px){
                    font-size: 3rem;
                }
            }
        }
        .buy-now-btn{
            text-align: center;
            button{
                border: none;
                color: white;
                font-size: 1.5rem;
                text-transform: uppercase;
                padding: 20px 40px;
                background: #333139;
                border-radius: 100px;
                letter-spacing: 1px;
                cursor: pointer;
                &:hover{
                    background: white;
                    color: black;
                }
            }
        }
    }
</style>