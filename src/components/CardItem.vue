<template>
    <div :class="dataSoldOut ? 'card-list__item' : 'card-list__item card-list__item_active'">
        <div class="card-list__sale">{{sale}}</div>
        <img @click="like" src="../assets/like.svg" alt="" :class="dataLiked ? 'card-list__like card-list__like_liked' : 'card-list__like'">
        <img class="card-list__img" :src="require(`@/assets/${img}`)" alt="">
        <div class="card-list__about">
            <h4 class="card-list__heading">{{name}}</h4>
            <div class="card-list__description">
                <span class="color">{{color}}<br> окрас</span>
                <span class="age"><strong>{{age}}</strong><br> Возраст</span>
                <span class="legs"><strong>{{legs}}</strong><br>Кол-во лап</span>
            </div>
            <div class="card-list__price">{{price}}</div>
        </div>
        <button :disabled="dataSoldOut ? 'disabled' : ''" :style="dataSoldOut ? {backgroundColor: 'var(--black)', cursor: 'default'} : {backgroundColor: 'var(--blue)'}" class="card-list__button">{{dataSoldOut ? 'Продано' : 'Купить'}}</button>
    </div>
</template>

<script>
export default {
    mounted () {
        this.dataLiked = this.liked;
        this.dataSoldOut = this.soldOut
    },
    methods: {
        like() {
            this.dataLiked ? 
            this.dataLiked = false :
            this.dataLiked = true
        }
    },
    data() {
        return {
            dataLiked: null,
            dataSoldOut: null,
        }
    },
    name: "CardItem",
    props: {
        price: {
            type: String,
            default: '30 000 руб.' 
        },
        color: {
            type: String
        },
        age: {
            type: String
        },
        img: {
            type: String
        },
        soldOut: {
            type: Boolean,
        },
        liked: {
            type: Boolean,
        },
        sale: {
            type: String,
        },
        name: {
            type: String,
        },
        legs: {
            type: Number,
        }

    },
}
</script>
<style scoped>
    .card-list__sale {
        position: absolute;
        top: 35px;
        left: 35px;
        background-color: var(--red);
        padding: 9px 18px;
        border-radius: 10px;
        color: #fff;
    }
    .card-list__like {
        position: absolute;
        right: 35px;
        top: 35px;
        cursor: pointer;
        transition: .4s ease all;
        opacity: 0.5;
        -webkit-tap-highlight-color: transparent;
    }

    .card-list__like:hover {
        transform: scale(1.2);
    }
    .card-list__like_liked {
        opacity: 1;
    }
    .card-list__button {
        border: none;
        width: 100%;
        padding: 20px 55px;
        text-align: center;
        color: #fff;
        font-weight: bold;
        border-radius: 0px 0px 15px 15px;
        cursor: pointer;
        border: 1px solid transparent;
        transition: 0.4s ease all;
        background: blue;
   }
   .card-list__button:hover {
       background: light-blue;
   }
    .card-list__button:focus {
        outline: none;
    }
    .card-list__item_active .card-list__button:hover {
        border: 1px solid lightblue;
        border: 1px solid var(--blue);
        background: #fff !important;
        color: lightblue;
        color: var(--blue);
    }
    .card-list__item {
        background-color: var(--gray);
        border-radius: 0px 0px 15px 15px;
        position: relative;
        display: inline-block;
    }
    .card-list__description {
        display: flex;
        justify-content: space-around;
        position: relative;
        margin: 25px 0;
    }
    .card-list__description::before {
        content: '';
        position: absolute;
        width: 4px;
        background-color: var(--blue);
        height: 100%;
        left: 0;
    }
    .card-list__about {
        width: 80%;
        margin: 30px auto;

    }
    .card-list__heading {
        font-weight: 700;
        font-size: 24px;
    }
    .card-list__price {
        font-weight: 700;
        font-size: 24px;
    }
    .card-list__img {
        width: 100%;
        display: block;
    }
</style>