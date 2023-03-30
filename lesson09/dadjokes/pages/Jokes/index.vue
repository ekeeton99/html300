<template>
    <div>
        <searchJokes v-on:search-text="search-text" />
        <Joke v-for="joke in jokes"
        :key="joke.id"
        :id="joke.id"
        :joke="joke.joke" />
    </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke";
import searchJokes from "../../components/searchJokes";

export default {
    components: {
        Joke,
        searchJokes
    },
    data() {
        return {
            jokes: []
        };
    },
    async created() {
        const config = {
            headers: {
                Accept: "application/json"
            }
        };

        try {
            const res = await axios.get('https://icanhazdadjoke.com/search', config);
            this.jokes = res.data.results;
        } catch(error) {
            console.log(error);
        }
    },
    methods: {
        async searchText(text) {
            const config = {
                headers: {
                    Accept: "application/json"
                }
            };
            try {
                const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
                this.jokes = res.data.results;
            } catch (err) {
                console.log(err);
            }
        }
    },
    head() {
        return {
            title: "Jokes",
            meta: [
                {
                    hid: "description",
                    name: "description",
                    content: "Best place for corny dad jokes"
                }
            ]
        }
    }
}
</script>