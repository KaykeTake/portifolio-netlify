<template>
    <!-- Configurações do perfil -->
    <v-navigation-drawer width="440" app v-model="drawer" temporary absolute>
        <v-list-item title="Perfil" height="100">
            <template v-slot:prepend>
                <v-btn @click.stop="drawer = !drawer" icon variant="text"
                    :ripple="false"><v-icon>mdi-arrow-left</v-icon></v-btn>
            </template>
        </v-list-item>
        <v-divider></v-divider>
        <div :style="{ 'padding': '1rem', 'display': 'flex', 'justify-content': 'center' }">
            <v-avatar size="200"><v-img src="../assets/eu e calopsita.jpg"></v-img></v-avatar>
        </div>
        <p :style="{ 'font-size': '0.9rem', 'padding': '1rem' }">Seu nome</p>
        <div :style="{ 'display': 'flex', 'align-items': 'center' }">
            <v-text-field :disabled="textfieldName" variant="underlined"></v-text-field>
            <v-btn v-if="textfieldName === false" icon variant="text"><v-icon>mdi-emoticon-excited-outline</v-icon></v-btn>
            <v-btn size="small" @click="toggleEditable('name')" icon variant="text"><v-icon
                    v-if="textfieldName === true">mdi-pencil</v-icon><v-icon
                    v-if="textfieldName === false">mdi-check</v-icon></v-btn>
        </div>
        <p :style="{ 'text-align': 'center' }">Esse não é seu nome de usuário e nem seu PIN. Esse nome será exibido para
            seus
            contatos do WhatsApp.</p>
        <p :style="{ 'font-size': '0.9rem', 'padding': '1rem' }">Recado</p>
        <div :style="{ 'display': 'flex', 'align-items': 'center' }">
            <v-text-field :disabled="textfieldNote" variant="underlined"></v-text-field>
            <v-btn v-if="textfieldNote === false" icon variant="text"><v-icon>mdi-emoticon-excited-outline</v-icon></v-btn>
            <v-btn size="small" @click="toggleEditable('note')" icon variant="text"><v-icon
                    v-if="textfieldNote === true">mdi-pencil</v-icon><v-icon
                    v-if="textfieldNote === false">mdi-check</v-icon></v-btn>
        </div>
    </v-navigation-drawer>
    <!-- //////Configurações do perfil -->

    <div :style="{ 'display': 'flex' }">

        <!-- Lado esquerdo -->
        <div :style="{ 'width': '440px', 'height': '100vh' }">
            <div
                :style="{ 'display': 'flex', 'justify-content': 'space-between', 'alignItems': 'center', 'padding-right': '1rem', 'height': '4rem', 'margin-left': '1rem' }">
                <v-btn @click.stop="drawer = !drawer" rounded="xl" icon><v-avatar size="45"><v-img
                            src="../assets/eu e calopsita.jpg"></v-img></v-avatar></v-btn>
                <div :style="{ 'display': 'flex', 'gap': '1rem' }">
                    <v-btn density="comfortable" variant="plan" icon>
                        <v-icon>mdi-account-group-outline</v-icon>
                    </v-btn>
                    <v-btn density="comfortable" variant="plan" icon>
                        <v-icon>mdi-chart-donut-variant</v-icon>
                    </v-btn>
                    <v-btn density="comfortable" variant="plan" icon>
                        <v-icon>mdi-tab-plus</v-icon>
                    </v-btn>
                    <v-btn density="comfortable" variant="plan" icon>
                        <v-icon>mdi-cloud-search-outline</v-icon>
                    </v-btn>
                    <v-btn density="comfortable" variant="plan" icon>
                        <v-icon>mdi-dots-vertical</v-icon>
                    </v-btn>
                </div>
            </div>

            <v-divider></v-divider>

            <!-- Pesquisa e Conversas -->
            <div :style="{ 'padding': '1rem' }">
                <v-text-field @focus="textfieldSearch = false" @blur="textfieldSearch = true" ref="textField"
                    label="Pesquisar ou começar uma nova conversa" variant="solo" density="compact" single-line hide-details
                    append-icon="mdi-filter-variant">
                    <template v-slot:prepend-inner>
                        <v-btn @click="textFieldFocus" v-if="textfieldSearch === true" icon variant="text"
                            size="small"><v-icon>mdi-magnify</v-icon></v-btn>
                        <v-btn @click="textFieldBlur" v-if="textfieldSearch === false" icon variant="text"
                            size="small"><v-icon>mdi-arrow-left</v-icon></v-btn>
                    </template>
                </v-text-field>
            </div>
            <v-list density="compact" nav>
                <v-hover>
                    <template v-slot:default="{ isHovering, props }">
                        <v-list-item v-bind="props" color="primary" class="w-100">
                            <template v-slot:prepend>
                                <v-avatar color="grey-darken-3" image=""></v-avatar>
                            </template>

                            <v-list-item-title>JavaScript</v-list-item-title>

                            <v-list-item-subtitle>oiiii! Tais sumido em</v-list-item-subtitle>

                            <template v-slot:append>
                                <div :style="{ 'display': 'flex', 'flex-direction': 'column', 'align-items': 'flex-end' }">
                                    <p>09:20</p>
                                    <div :style="{ 'display': 'flex', 'align-items': 'center', 'gap': '0.4rem' }">
                                        <v-icon>mdi-volume-off</v-icon>
                                        <v-chip color="green">300</v-chip>
                                        <v-expand-transition>
                                            <v-icon v-if="isHovering === true">mdi-chevron-down</v-icon>
                                        </v-expand-transition>
                                    </div>
                                </div>
                            </template>
                        </v-list-item>
                    </template>
                </v-hover>
            </v-list>
            <!-- Pesquisa e Conversas -->
        </div>
        <!-- //////Lado esquerdo -->

        <!-- lado direito -->
        <div :style="{ 'flex': '1', 'display': 'flex', 'flex-direction': 'column' }">
            <v-sheet height="4rem" color=""
                :style="{ 'display': 'flex', 'align-items': 'center', 'justify-content': 'space-between' }">
                <div :style="{ 'display': 'flex', 'align-items': 'center', 'gap': '1rem', 'margin-left': '1rem' }">
                    <v-avatar color="grey-darken-3" image=""></v-avatar>
                    <div>
                        <v-list-item-title>JavaScript</v-list-item-title>
                        <v-list-item-subtitle>Online</v-list-item-subtitle>
                    </div>
                </div>
                <div :style="{ 'display': 'flex', 'align-items': 'center', 'gap': '1rem', 'margin-right': '1rem' }">
                    <v-btn rounded="xl" prepend-icon="mdi-video-outline"><v-icon>mdi-chevron-down</v-icon></v-btn>
                    <v-icon>mdi-magnify</v-icon>
                    <v-icon>mdi-dots-vertical</v-icon>
                </div>
            </v-sheet>
            <v-sheet class="chat" color="white">
                <div v-for="ballon in chats" :key="ballon.id">
                    <div v-if="ballon.sender === true"
                        :style="{ 'background-color': 'green', 'max-width': '200px', 'word-break': 'break-word', 'border-radius': '1rem', 'padding': '0.8rem' }">
                        {{ballon.text}}
                    </div>
                    <div v-if="ballon.sender === false" :style="{ 'width': '100%', 'display': 'flex', 'justify-content': 'flex-end' }">
                        <div
                            :style="{ 'background-color': 'green', 'max-width': '200px', 'word-break': 'break-word', 'border-radius': '1rem', 'padding': '0.8rem' }">
                            {{ballon.text}}
                        </div>
                    </div>
                </div>
            </v-sheet>
            <v-sheet height="4rem" :style="{ 'padding': '1rem' }">
                <v-text-field label="Digite uma mensagem" variant="solo" density="compact" single-line hide-details>
                    <template v-slot:prepend>
                        <div :style="{ 'display': 'flex', 'gap': '0.5rem' }">
                            <v-icon size="x-large">mdi-emoticon-excited-outline</v-icon>
                            <v-icon size="x-large">mdi-plus</v-icon>
                        </div>
                    </template>
                    <template v-slot:append>
                        <v-icon size="x-large">mdi-microphone</v-icon>
                    </template>
                </v-text-field>
            </v-sheet>
        </div>
        <!-- ////lado direito -->
    </div>
</template>
<script setup>
import { ref } from 'vue'
let chats = [
    {
     text: 'oi',
     id: 1,
     sender: true
    },
    {
     text: 'oiiiiiiiiiiiiiiiiiiiii',
     id: 2,
     sender: false
    }
]
let drawer = ref(null)
let textfieldSearch = ref(true)
let textfieldName = ref(true)
let textfieldNote = ref(true)
const toggleEditable = (data) => {
    if (data === 'name') {
        textfieldName.value = !textfieldName.value
        return
    } else if (data === 'note') {
        textfieldNote.value = !textfieldNote.value
    }
}
const textFieldFocus = () => {
    this.$refs.textField.focus()
}
const textFieldBlur = () => {
    this.$refs.textField.blur()
}
</script>
<style scoped>
.chat {
    flex: 1;
    background-image: url(../assets/back.jpg);
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
}
</style>