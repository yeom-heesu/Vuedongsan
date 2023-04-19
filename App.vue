<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

</script>

<template>
    <header>
        <div class = "black-bg" v-if="m_open">
            <div class = "white-bg">
                <h4></h4>
                <p>상세페이지 내용</p>
                <button @click="m_open = false">닫기</button>
            </div>
        </div>

        <div class="menu">
            <a v-for="a in menus" :key="i">{{ a }} </a>
            <br><br><br><br>
<!--            <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125"/>-->
        </div>



        <div class="room-img" v-for="(a,i) in datas" :key="i">
            <img v-bind:src="a.image" >
            <h4 v-on:click="modal">{{a.title}}</h4>
            <p> {{ a.price }} 원 </p>
        <button v-on:click="addsingo(i)">허위매물신고</button> <span> 신고수 : {{singo[i]}}</span>
        </div>

<!--        <div class = "room-img">-->
<!--            <img src = "./assets/room0.jpg">-->
<!--            <h4 v-on:click="modal">{{datas[0].title}}</h4>-->
<!--            <p>50만원</p>-->
<!--            <button v-on:click="addsingo(0)">허위매물신고</button> <span> 신고수 : {{singo[0]}}</span>-->
<!--        </div>-->
<!--        <div class = "room-img">-->
<!--            <img src = "./assets/room1.jpg">-->
<!--            <h4 v-on:click="modal">{{products[1]}}</h4>-->
<!--            <p>60만원</p>-->
<!--            <button v-on:click="addsingo(1)">허위매물신고</button> <span> 신고수 : {{singo[1]}}</span>-->
<!--        </div>-->
<!--        <div class = "room-img">-->
<!--            <img src = "./assets/room2.jpg">-->
<!--            <h4 v-on:click="modal">{{products[2]}}</h4>-->
<!--            <p>70만원</p>-->
<!--            <button v-on:click="addsingo(2)">허위매물신고</button> <span> 신고수 : {{singo[2]}}</span>-->
<!--        </div>-->
    </header>
</template>

<script>
import datas from './assets/oneroom.js';

export default {
    name: 'App',
    data() {
        return {
            onerooms : datas,
            m_open : false,
            singo : [0,0,0,0,0,0] ,
            menus: ["Home", "products", "About"],
        }
    },
    methods : {
        addsingo(index) {
            this.singo[index] ++;
        },
        modal(){
            this.m_open = true;
        }
    }
}
</script>
<style scoped>
header {
    line-height: 1.5;
}

.logo {
    display: block;
    margin: 0 auto 2rem;
}
.menu a {
    color: white;
    padding: 10px;
}
.room-img {
    width: 100%;
    margin-top: 40px;
}
.black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0,5);
    position: fixed; padding : 20px;
}
.white-bg {
    width: 100%;
    background: white;
    border-radius: 8px;
    padding: 20px;
}
@media (min-width: 1024px) {
    header {
        display: flex;
        place-items: center;
        padding-right: calc(var(--section-gap) / 2);
    }


    header .wrapper {
        display: flex;
        place-items: flex-start;
        flex-wrap: wrap;
    }

    .menu {
        background: darkslateblue;
        padding: 15px;
        border-radius: 5px;
    }


}
</style>
