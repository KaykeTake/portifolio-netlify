<template>
    <div class="main-container">
        <header>
            <div class="header-box">
                <h1 class="myName">Anderson Kayke</h1>
                <nav>
                    <ul>
                        <a href="#">{{ chevron }} Services /></a>
                        <a href="#">{{ chevron }} Works /></a>
                        <a href="#">{{ chevron }} Notes /></a>
                        <a href="#">{{ chevron }} Contact /></a>
                    </ul>
                </nav>
            </div>
            <nav>
                <ul class="ul-social">
                    <a><v-tooltip activator="parent" location="bottom">Not Found
                            404</v-tooltip><v-icon>mdi-gmail</v-icon>Gmail</a>
                    <a href="https://www.linkedin.com/in/anderson-kayke/"><v-icon>mdi-linkedin</v-icon>LinkedIn</a>
                    <a href="https://github.com/KaykeTake"><v-icon>mdi-github</v-icon>GitHub</a>
                </ul>
            </nav>
        </header>
        <div class="bottom-container">
            <div class="info-container">
                <div :style="{ 'display': 'flex', 'flex-direction': 'column', 'gap': '1rem' }">
                    <p class="front-end">
                        Front-End Developer
                    </p>
                    <p class="info">Programming your <br /> <i>EXPERIENCE.</i> </p>
                    <p>I design and code beautifully simple thing <br /> and i love what i do</p>
                </div>
                <a :style="{ 'font-size': 'xx-large', 'text-decoration': 'underline', 'font-family': 'Salsa' }"
                    color="#4BAFEB" href="/projects">See
                    my Projects!</a>
                <div class="rodape">
                    <div class="number-text">
                        <p class="number">01</p>
                        <p>YEARS OF <br />EXPERIENCE</p>
                    </div>
                    <div class="number-text">
                        <p class="number">3</p>
                        <p>PROJECTS <br />CREATED</p>
                    </div>
                </div>
            </div>
            <div v-if="!isMobile" :style="{ 'display': 'flex', 'align-items': 'center' }">
                <div class="backgroung-ball">
                    Imagine My Picture here
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
const chevron = '<'
let isMobile = ref(null);

const checkMobile = () => {
    isMobile.value = window.innerWidth <= 1300; // ou outro valor de largura que você considere como "móvel"
    if (isMobile.value) {
        console.log('oi');
    }
}

onMounted(() => {
    checkMobile();
    window.addEventListener('resize', checkMobile);
});
</script>


<style scoped>
.main-container {
    height: 100vh;
    background: linear-gradient(to bottom right, rgb(22, 22, 22), #0D0321);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.myName {
    font-family: 'Salsa';
}

header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.4rem;
}


.header-box {
    display: flex;
    align-items: center;
    gap: 7rem;
}

header nav {
    display: flex;
}

header nav ul {
    display: flex;
    gap: 1.5rem;
}

.ul-social {
    gap: 7rem;
}

a {
    text-decoration: none;
    color: inherit;
    cursor: pointer;
    transition: color 0.3s, transform 0.3s;
    display: flex;
    align-items: center;
    font-family: 'Salsa';
}

a:hover {
    color: aqua;
    transform: scale(1.1);
}

p {
    font-family: 'Playfair Display';
}

.bottom-container {
    flex: 1;
    display: flex;
    justify-content: space-around;
}

.info-container {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
}

.front-end {
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    border-radius: 10px;
    width: 250px;
    height: 50px;
    background-color: #4BAFEB;
    color: #0D0321;
    font-size: x-large;
    display: flex;
    justify-content: center;
    align-items: center;
}

.info {
    font-size: 3em;
}

.rodape {
    display: flex;
    font-size: x-large;
    gap: 6rem;
}

.number-text {
    display: flex;
    align-items: center;
}

.number {
    font-size: 4rem;
}

.backgroung-ball {
    width: 600px;
    height: 600px;
    background: linear-gradient(to bottom right, rgb(22, 22, 22), #0D0321);
    border-radius: 50%;
}

@media screen and (max-width: 1300px) {
    header {
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .ul-social {
        gap: 2rem;
    }
    .number-text {
    display: flex;
    align-items: center;
    flex-direction: column;
}
.header-box{
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 1rem;
}
}
</style>
