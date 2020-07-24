<template>
    <div class="SendMessage">
        <form @submit="sendNewMessage">
            <p>Username:
                <input type="text" v-model="user">
            </p>
            <p>Message:
                <textarea v-model="message"></textarea>
            </p>
            <button class="btn btn-success">Send</button>
        </form>
    </div>
</template>

<script>
    import axios from 'axios'
    
    export default {
        name: 'SendMessage',
        data() {
            return {
                user: null,
                message: null
            }
        },
        mounted() {
            console.log('SendMessage mounted')
        },
        methods: {
            sendNewMessage(e) {
                e.preventDefault();
                axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*';
                axios
                    .post('http://localhost:8080/messages', {
                        user: this.user,
                        message: this.message
                    })
                    .then(response => {
                        console.log(response.data)
                    })
            }
        }
    }
</script>
