<template>
    <section class="card-list-section">
         <div class="sort">
            <h4>Сортировать по:</h4>
            <span :style="sortedByPrice ? {fontWeight: 'bold'} : ''" @click="priceSort" class="price-sort">Цене <i :class="sortedByPriceUp ? 'fas fa-chevron-up' : 'fas fa-chevron-down'"></i></span>
            <span :style="sortedByAge ? {fontWeight: 'bold'} : ''" @click="ageSort" class="age-sort">Возрасту <i :class="sortedByAgeUp ? 'fas fa-chevron-up' : 'fas fa-chevron-down'"></i></span>
        </div>
        <div class="card-list">
            <CardItem 
            :key="index"
            :name="item.name"
            :legs="item.legs"
            :soldOut="item.soldOut"
            :liked="item.liked"
            :price="item.price"
            :color="item.color"
            :img="item.img"
            :sale="item.sale"
            :age="item.age"
            v-for="(item, index) in showList"/>
        </div>
        <button @click="add" v-if="quantityToAdd" class="more-button">Показать еще {{addQuantity}}</button>
    </section>
</template>
<script>
import listData from '../data.json'
import CardItem from './CardItem.vue'
export default {
    methods: {
        add: async function() {
           this.showList = this.listData;
           this.quantityToAdd = 0;
           await this.$nextTick()
        },
        priceSort() {
            if (!this.sortedByPrice) {
                this.sortedByPrice = true;
                this.sortedByAge = false;
            }
            this.sortedByPriceUp = !this.sortedByPriceUp
            if  (this.sortedByPriceUp) {
                this.showList.sort((a, b) => {
                    if (a.priceValue >= b.priceValue) {
                        return 1;
                    } else {
                        return -1;
                    }
                })
            } else {
                 this.showList.sort((a, b) => {
                    if (a.priceValue < b.priceValue) {
                        return 1;
                    } else {
                        return -1;
                    }
                })
            }
        },
        ageSort() {
            if(!this.sortedByAge) {
                this.sortedByAge = true;
                this.sortedByPrice = false;
            }
            this.sortedByAgeUp = !this.sortedByAgeUp
            if  (this.sortedByAgeUp) {
                this.showList.sort((a, b) => {
                    if (a.ageValue >= b.ageValue) {
                        return 1;
                    } else {
                        return -1;
                    }
                })
            } else {
                 this.showList.sort((a, b) => {
                    if (a.ageValue < b.ageValue) {
                        return 1;
                    } else {
                        return -1;
                    }
                })
            }
        }
    },
    mounted () {

        this.listData = listData;
        this.showList = this.listData.slice(0, 6);
        console.log()
        console.log(listData)
        this.quantityToAdd = this.addQuantity;
        this.priceSort();
    },
    data() {
        return {
            listData: null,
            showList: null,
            quantityToAdd: null,
            sortedByAge: false,
            sortedByPrice: true,
            sortedByAgeUp: false,
            sortedByPriceUp: true,
        }
    },
    name: 'CardList',
    props: {
        addQuantity: {
            type: Number,
        },
    },
    components: {
        CardItem,
    }
}
</script>
<style>
.more-button {
    text-align: center;
    border: 1px solid #cacaca;
    background-color: transparent;
    width: 380px;
    margin: 80px 0 0;
    border-radius: 10px;
    padding: 25px 0;
    cursor: pointer;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    transition: .4s ease all;
}
.more-button:hover {
    background-color: var(--blue);
    border: 1px solid var(--blue);
    color: #fff;
}
.more-button:focus {
    outline: none;
}
.card-list-section {
    max-width: 1280px;
    margin: 45px auto 0;
}
.card-list {
    max-width: 1280px;
    margin: 40px auto 0;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 25px 20px;
}
.sort h4 {
    display: inline-block;
    margin-right: 45px;
}
.sort span {
    cursor: pointer;
}
span i {
    margin-left: 7px;
    margin-right: 50px;
}
@media screen and (max-width: 1280px) {
    .card-list {
        grid-template-columns: 1fr 1fr;
    }
}
@media screen and (max-width: 900px) {
    .card-list {
        grid-template-columns: 1fr;
    }
}
@media screen and (max-width: 525px) {
    .sort h4 {
        display: block;
    }
    .sort {
        text-align: center;
    }
}
</style>