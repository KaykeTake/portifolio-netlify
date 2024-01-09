<template>
    <v-sheet width="90%" class="mx-auto" color="white" :style="{ 'padding': '40px' }">
        <v-container fluid fill-height>
            <v-row align="center" justify="center">
                <v-col cols="12" sm="8" md="6" lg="4">
                    <v-card class="mx-auto px-16 py-8">
                        <div :style="{ 'display': 'flex', 'flex-direction': 'column', 'align-items': 'center' }">
                            <v-icon>mdi-fire</v-icon>
                            <p>WELCOME BACK</p>
                        </div>
                        <form> <v-text-field color="primary" width="100%" variant="underlined" label="Email"
                                prepend-inner-icon="mdi-email-outline" :rules="email" required></v-text-field> <v-text-field
                                color="primary" :type="visible ? 'text' : 'password'" width="100%" variant="underlined"
                                :counter="10" :rules="password" label="Password" prepend-inner-icon="mdi-lock-outline"
                                :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
                                @click:append-inner="visible = !visible" required></v-text-field>
                            <div :style="{ 'display': 'flex', 'justify-content': 'flex-end' }"><a
                                    class="text-blue text-decoration-none" href="#" rel="noopener noreferrer"
                                    target="_blank"> Forgot Password? </a></div> <v-btn class="button" rounded="xl" block
                                color="success">Login</v-btn>
                        </form> <v-btn prepend-icon="mdi-google" class="button" rounded="xl" color="white" block>Login with
                            google</v-btn>
                        <div :style="{ 'display': 'flex', 'gap': '1rem', 'justify-content': 'center' }">
                            <p>don't have an account?</p> <a class="text-blue text-decoration-none" href="#"
                                rel="noopener noreferrer" target="_blank"> Sign up </a>
                        </div>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </v-sheet>
</template>
<script>
export default {
    data: () => ({
        visible: false,
        password: [
            value => {
                if (value?.length > 10) return true

                return 'Password must be at least 10 characters.'
            },
        ],
        email: [
            value => {
                if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true

                return 'Must be a valid e-mail.'
            }
        ]
    }),
    methods: {
        submit(values) {
            alert(JSON.stringify(values, null, 2))
        }

    }
}
</script>
<style scoped>
.button {
    margin: 10px 0px 10px 0px;
}
</style>