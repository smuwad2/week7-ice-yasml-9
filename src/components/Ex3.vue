<script>
// import axios from 'axios';

    export default { 

       // add code here
       data() {
        return {
            moods: ["happy", "sad", "angry"],
            setMood: '',
            subject: '',
            entry: '',
            outputMessage : ""
        }
       },
       computed: {
        baseUrl() {
            if (window.location.hostname === 'localhost') {
                console.log("hello");
                return "http://localhost:3000";
            } else {
                const codespace_host = window.location.hostname.replace('5173', '3000')
                return `https://${codespace_host}`;
            }
        }
       },
       methods: {
        addPost() {
            axios.get(`${this.baseUrl}/addPost`, {
                params: {
                    "subject": this.subject,
                    "entry": this.entry,
                    "mood": this.setMood
                }
            }) .then (response => {
                this.outputMessage = response.data.message;
            }) .catch (err => {
                console.log(err);
            });
        }
       }

    }
</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->
         <select v-model="setMood">
            <option v-for="mood in this.moods"> {{ mood }}</option>
         </select>

        <br>

        <br>
        <button @click="addPost()">Submit New Post</button>

        <hr> Click  <a><router-link to="/ViewPosts/">here</router-link></a>  to return to Main Page

        <h1 v-if="outputMessage" style="position: fixed; top: 0; border: 1px solid green; border-radius: 5px; color: red;">{{ outputMessage }}</h1>
       
    </div>
</template>

