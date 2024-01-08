<template>
    <v-sheet class="mx-auto" width="90%" color="white" :style="{ 'padding': '40px' }">
        <v-layout>
            <v-app-bar color="primary" density="compact">
                <template v-slot:prepend>
                    <v-app-bar-nav-icon></v-app-bar-nav-icon>
                </template>

                <v-app-bar-title>Tickets</v-app-bar-title>

                <template v-slot:append>
                    <v-menu transition="slide-y-transition" :close-on-content-click="false">
                        <template v-slot:activator="{ props }">
                            <v-btn v-bind="props" icon="mdi-cart-outline"></v-btn>
                        </template>
                        <v-list>
                            <v-list-subheader>Ticket's cart</v-list-subheader>
                            <v-list-item v-for="ticket in ticketsCart" :key="ticket.id">
                                <v-list-item-title>{{ ticket.ticket }}</v-list-item-title>
                                <template v-slot:append>
                                    <v-btn color="grey-lighten-1" @click="more(ticket.id)" icon="mdi-plus"
                                        variant="text"></v-btn>
                                    <p>{{ ticket.amount }}</p>
                                    <v-btn color="grey-lighten-1" @click="less(ticket.id)" icon="mdi-minus"
                                        variant="text"></v-btn>
                                </template>
                            </v-list-item>
                        </v-list>
                    </v-menu>
                </template>
            </v-app-bar>

            <v-main>
                <v-container fluid>
                    <v-row dense>
                        <v-col v-for="(ticket, id) in tickets" :key="id" cols="6">
                            <v-sheet color="surface-variant-alt" min-height="100"
                                :style="{ 'display': 'flex', 'flex-direction': 'column', 'justify-content': 'space-between' }">
                                <p :style="{ 'text-align': 'center' }">{{ ticket.text }}</p>
                                <v-divider></v-divider>
                                <p :style="{ 'text-align': 'center' }">Amount: {{ ticket.amount }}</p>
                                <v-btn rounded="0" :disabled="isDisabled(ticket)" color="success" width="100%"
                                    @click="addToCart(ticket.id)">
                                    Add to cart
                                </v-btn>
                            </v-sheet>
                        </v-col>
                    </v-row>
                </v-container>
            </v-main>
        </v-layout>
    </v-sheet>
</template>
  
<script>
export default {
    data: () => ({
        tickets: [
            { id: 1, text: 'I need coffee: The film', amount: 3, disabled: false },
            { id: 2, text: 'The Python', amount: 3, disabled: false },
            { id: 3, text: 'Lord of JavaScript', amount: 3, disabled: false },
            { id: 4, text: 'JAVA (Musical)', amount: 3, disabled: false }
        ],
        ticketsCart: []
    }),
    methods: {
        addToCart(id) {
            const selectedTicket = this.tickets.find(ticket => ticket.id === id)
            const existingTicket = this.ticketsCart.find(cartItem => cartItem.id === id)

            if (!selectedTicket.amount <= 0) {
                if (existingTicket) {
                    existingTicket.amount++
                    selectedTicket.amount--
                } else {
                    this.ticketsCart.push({
                        id: selectedTicket.id,
                        ticket: selectedTicket.text,
                        amount: 1
                    });
                    selectedTicket.amount--
                }
            }
        },
        more(id) {
            const selectedTicket = this.tickets.find(ticket => ticket.id === id)

            if (!selectedTicket.amount <= 0) {
                const existingTicket = this.ticketsCart.find(cartItem => cartItem.id === id)
                if (existingTicket) {
                    existingTicket.amount++
                    selectedTicket.amount--
                }
            }
        },
        less(id) {
            const selectedTicket = this.tickets.find(ticket => ticket.id === id)


            const existingTicket = this.ticketsCart.find(cartItem => cartItem.id === id)
            if (existingTicket) {
                existingTicket.amount--
                selectedTicket.amount++

                if (existingTicket.amount === 0) {
                    this.ticketsCart = this.ticketsCart.filter(cartItem => cartItem.id !== id)
                }
            }

        },
        isDisabled(ticket) {
            return ticket.amount === 0;
        }
    },
};
</script>
<style></style>
  