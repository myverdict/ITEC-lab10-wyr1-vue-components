<!-- this is the parent component of the WouldYouRather.vue -->

<template>
    <div id="app">
        <h1>Would you rather...</h1>

        <!-- this is being replaced by the WouldYouRather.vue template -->
        <!-- a vue component can have dashes, an html element does not have dashes -->
        <!-- the question, answer1, answer2 are from the props of the child WouldYouRather.vue -->
        <!-- the wyrQuestion, wyrAnswer1, wyrAnswer2 are from the data of the parent App.vue -->
        <!-- the answer-changed is from the choiceMade method of the child WouldYouRather.vue -->
        <!-- the answerChanged method is from the parent App.vue -->
        <would-you-rather v-bind:question="wyrQuestion"
                          v-bind:answer1="wyrAnswer1"
                          v-bind:answer2="wyrAnswer2"
                          v-on:answer-changed="answerChanged">    <!-- this is from the event changed in the radio buttons -->
        </would-you-rather>

        <!-- alternate way of writing the above tags/elements -->
        <!-- <WouldYouRather></WouldYouRather> -->

        <p>{{ userSelectionMessage }}</p>
    </div>
</template>

<script>
    import WouldYouRather from './components/WouldYouRather.vue'

    export default {
        name: 'App',
        components: {
            WouldYouRather
        },
        data() {
            return {
                wyrQuestion: 'Would you rather have a magic carpet that flies or a see-through submarine?',
                wyrAnswer1: 'Magic carpet that flies',
                wyrAnswer2: 'See-through submarine',
                userSelectionMessage: ''
            }
        },
        methods: {
            answerChanged(choice) {
                this.userSelectionMessage = `Thanks! you chose ${choice}`
            }
        }
    }
</script>

<style>
    body { background-color: lightseagreen; }
    #app
    {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
        background-color: teal;
        color: white;
        padding: 20px;
    }
</style>
