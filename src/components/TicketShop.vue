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
                            <v-list-item v-for="(ticket, index) in  ticketsCart " :key="ticket">
                                <v-list-item-title>{{ ticket.ticket }}</v-list-item-title>
                                <template v-slot:append>
                                    <v-btn color="grey-lighten-1" @click="more(index)" icon="mdi-plus"
                                        variant="text"></v-btn>
                                    <p>{{ ticket.amount }}</p>
                                    <v-btn color="grey-lighten-1" @click="less(index)" icon="mdi-minus"
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
                        <v-col v-for="(ticket, index) in  tickets " :key="index" cols="6">
                            <v-sheet color="surface-variant-alt" min-height="100"
                                :style="{ 'display': 'flex', 'flex-direction': 'column', 'justify-content': 'space-between' }">
                                <p :style="{ 'text-align': 'center' }">{{ ticket.text }}</p>
                                <v-divider></v-divider>
                                <p :style="{ 'text-align': 'center' }">Amount: {{ ticket.amount }}</p>
                                <v-btn rounded="0" :disabled="isDisabled(ticket)" color="success" width="100%"
                                    @click="addToCart(index)">
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
            { text: 'I need coffe: The film', amount: 3, disabled: false },
            { text: 'The Python', amount: 3, disabled: false },
            { text: 'Lord of JavaScript', amount: 3, disabled: false },
            { text: 'JAVA (Musical)', amount: 3, disabled: false }
        ],
        ticketsCart: []
    }),
    methods: {
        addToCart(index) {
            const selectedTicket = this.tickets[index]
            const existingTicketIndex = this.ticketsCart.findIndex(cartItem => cartItem.ticket === selectedTicket.text)
            if (!selectedTicket.amount <= 0) {
                if (existingTicketIndex !== -1) {
                    this.ticketsCart[existingTicketIndex].amount++
                    this.tickets[index].amount--
                } else {
                    this.ticketsCart.push({
                        ticket: selectedTicket.text,
                        amount: 1
                    });
                    this.tickets[index].amount--
                }
            }
        },
        more(index) {
            const selectedTicket = this.tickets[index]
            if (!selectedTicket.amount <= 0) {
                this.ticketsCart[index].amount++;
                this.tickets[index].amount--;
            }
        },
        less(index) {
            if (this.ticketsCart[index].amount > 0) {
                this.ticketsCart[index].amount--;
                this.tickets[index].amount++;
            }
        },
        isDisabled(ticket) {
            return ticket.amount === 0;
        }
    },
    computed: {
        updatedTickets() {
            return this.tickets.map(ticket => {
                return {
                    ...ticket,
                    disabled: ticket.amount === 0
                };
            });
        }
    }
}
</script>
<style></style>