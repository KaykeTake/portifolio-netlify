<template>
    <v-sheet class="mx-auto" width="90%" color="white" :style="{ 'padding': '40px' }">
        <v-card class="mx-auto" max-width="90%">
            <v-container fluid>
                <v-row dense>
                    <v-col :style="{ 'display': 'flex', 'justify-content': 'center' }">
                        TODO - LIST
                    </v-col>
                    <v-divider></v-divider>
                    <v-sheet class="mx-auto" height="250px" width="100%"
                        :style="{ 'overflow': 'hidden', 'overflow-y': 'auto' }">
                        <v-col v-for="(item, index) in list" :key="index" cols="12" :style="{ 'width': '100%' }">
                            <v-card :class="{ 'blue-card': item.checked }"
                                :style="{ 'display': 'flex', 'alignItems': 'center' }">
                                <v-checkbox v-model="item.checked" :label="item.text"></v-checkbox>
                                <v-icon :style="{ 'margin-right': '1rem' }" color="red" class="delete-icon"
                                    @click="deleteItem(index)">mdi-delete</v-icon>
                            </v-card>
                        </v-col>
                    </v-sheet>
                    <v-divider></v-divider>
                    <div :style="{ 'display': 'flex', 'flex-direction': 'column', 'width': '100%' }">

                        <v-textarea label="Write a new task" variant="outlined" rows="1" row-height="15" v-model="item"
                            @keydown.enter.prevent="addItem()"></v-textarea>
                        <v-col :style="{}">
                            <v-btn min-height="50px" block color="success" height="auto"
                                @click.prevent="addItem()">to add</v-btn>
                            <v-btn min-height="50px" block variant="outline" color="error" height="auto"
                                @click.prevent="deleteCompleted()">Remove completed</v-btn>
                        </v-col>
                    </div>
                </v-row>
            </v-container>
        </v-card>
    </v-sheet>
</template>
<script>
export default {
    data: () => ({
        list: [
            { text: 'Print helloWorld', checked: false },
            { text: 'Learn Java', checked: false },
            { text: 'Python is a snake or a programming language', checked: false }
        ],
        item: ''
    }),
    methods: {
        deleteItem(index) {
            this.list.splice(index, 1);
        },
        deleteCompleted() {
            this.list = this.list.filter((item) => item.checked !== true)
        },
        addItem() {
            if (this.item.trim() !== '') {
                this.list.unshift({ text: this.item, checked: false });
                this.item = ''
            }
        }
    }
}
</script>
<style scoped>
:deep(.v-input__details) {
    min-height: 0px !important;
    padding-top: 0px !important;
}

:deep(.v-messages) {
    min-height: 0px !important;
}

.blue-card {
    background-color: #58E06E;
    color: black;
    /* Adicione essa linha se quiser ajustar a cor do texto para melhor visibilidade */
}</style>