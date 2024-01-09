<template>
    <div
        :style="{ 'height': '100vh', 'display': 'flex', 'alignItems': 'center', 'justify-content': 'center', 'flex-direction': 'column', 'gap': '1rem' }">
        <div>
            <div :style="{ 'display': 'flex', 'alignItems': 'center', 'justifyContent': 'center', 'gap': '2rem' }">
                <v-avatar size="80"><v-img src="../assets/eu e calopsita.jpg"></v-img></v-avatar>
                <p :style="{ 'font-size': 'x-large' }"><strong>ANDERSON KAYKE</strong></p>
            </div>
        </div>
        <div>
            <div :style="{ 'display': 'flex', 'justify-content': 'center' }">
                <v-btn-toggle v-model="toggle" color="primary" mandatory>
                    <v-btn value="br" color="purple" max-width="0px" min-width="20px" max-height="20px"> <img width="20"
                            height="20" src="https://img.icons8.com/color/20/brazil.png" alt="brazil" /></v-btn>
                    <v-btn value="us" color="purple" max-width="0px" min-width="20px" max-height="20px"> <img width="20"
                            height="20" src="https://img.icons8.com/color/20/usa.png" alt="usa" /></v-btn>
                </v-btn-toggle>
            </div>
            <div
                :style="{ 'display': 'flex', 'justify-content': 'center', 'flex-direction': 'column', 'align-items': 'center', 'gap': '1rem' }">
                <p class="text" v-if="toggle === 'br'" :style="{ 'font-size': 'x-large' }"><strong>PROGRAMADOR
                        FRONT-END</strong></p>
                <p class="text" v-if="toggle === 'us'" :style="{ 'font-size': 'x-large' }"><strong>FRONT-END
                        PROGRAMMER</strong></p>
                <p class="text" v-if="toggle === 'br'">tecnologias | linguagens:</p>
                <p class="text" v-if="toggle === 'us'">technologies | languages:</p>
                <div :style="{ 'display': 'flex' }">
                    <v-tooltip text="JavaScript" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30"
                                src="https://img.icons8.com/color/30/javascript--v1.png" alt="javascript--v1" />
                        </template>
                    </v-tooltip>
                    <v-tooltip text="Html-5" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30" src="https://img.icons8.com/color/30/html-5--v2.png"
                                alt="html-5--v2" />
                        </template>
                    </v-tooltip>
                    <v-tooltip text="Css-3" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30" src="https://img.icons8.com/fluency/30/css3.png"
                                alt="css3" />
                        </template>
                    </v-tooltip>
                    <v-tooltip text="Vue.js" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30" src="https://img.icons8.com/color/30/vue-js.png"
                                alt="vue-js" />
                        </template>
                    </v-tooltip>
                    <v-tooltip text="Vuetify" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30"
                                src="https://img.icons8.com/windows/30/000000/vuetify.png" alt="vuetify" />
                        </template>
                    </v-tooltip>
                    <v-tooltip text="Python" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30" src="https://img.icons8.com/color/30/python--v1.png"
                                alt="python--v1" />
                        </template>
                    </v-tooltip>
                    <v-tooltip text="Git" location="top">
                        <template v-slot:activator="{ props }">
                            <img v-bind="props" width="30" height="30" src="https://img.icons8.com/badges/30/git.png"
                                alt="git" />
                        </template>
                    </v-tooltip>
                </div>
                <p class="text" v-if="toggle === 'br'">SOBRE MIM</p>
                <p class="text" v-if="toggle === 'us'">ABOUT ME</p>
                <p class="text" v-if="toggle === 'br'">Atualmente apenas vagando no ecosistema em busca de um emprego</p>
                <p class="text" v-if="toggle === 'us'">Currently just wandering in the ecosystem in search of a job</p>
            </div>

        </div>
        <div :style="{ 'display': 'flex', 'justify-content': 'center', 'gap': '2rem' }">
            <a href="https://github.com/KaykeTake"> <img
                    src="https://img.shields.io/badge/-Github-blue?style=flat-square&logo=github&logoColor=white"
                    alt="linkedin" /></a>
            <a href="https://www.linkedin.com/in/anderson-kayke/"> <img
                    src="https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white"
                    alt="linkedin" /> </a>
            <a href="https://resume.io/r/Gz0lu1BbX"> <img
                    src="https://camo.githubusercontent.com/e37091747d316cd7484f805586e492516080325e316c063eb194c8451681e035/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2d726573756d652d696e666f726d6174696f6e616c3f7374796c653d666c61742d737175617265"
                    alt="resume" /> </a>

        </div>
        <div class="icon-mouse">
            <v-icon>mdi-mouse</v-icon>
        </div>
    </div>
</template>
<script>
export default {
    data: () => ({
        toggle: 'br',
    })
}
</script>
<style scoped>
.text {
    text-align: center;
}

.icon-mouse {
    margin-top: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
}

.icon-mouse .v-icon {
    transition: transform 0.3s ease-in-out;
    animation: bounceUpDown 2s infinite;
}

@keyframes bounceUpDown {

    0%,
    100% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(-10px);
    }
}
</style>