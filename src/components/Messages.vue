<template>
    <div class="Messages">
        <button v-on:click="getNewMessages">Get New Messages</button>
        <table>
            <tbody>
                <th>ID</th>
                <th>User</th>
                <th>Message</th>
                <tr v-for="message in messages" :key="message.id">
                    <td>{{ message.id }}</td>
                    <td>{{ message.user }}</td>
                    <td>{{ message.content }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    import axios from 'axios'
    
    export default {
        name: 'Messages',
        data() {
            return {
                messages:null
            }
        },
        mounted() {
            console.log('Messages mounted')
        },
        methods: {
            getNewMessages() {
                axios
                    .get('http://localhost:8080/messages')
                    .then(response => {
                        this.messages = response.data
                    })
            }
        }
    }
</script>
