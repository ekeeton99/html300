<template>
    <div>
        <Joke />
    </div>
</template>

<script>
// import axios from "axios";
import Joke from "../../components/Joke";

export default {
    components: {
        Joke
    },
//     data() {
//         return {
//             jokes: []
//         };
//     },
    // mounted() {
    //     axios
    //         .get('https://icanhazdadjoke.com/search')
    //         .then(response => (this.jokes = response.data.results))
    //         .catch(error => {
    //             console.log(error)
    //         })
    //         .finally(() => this.loading = false)
    // },
    // async created() {
    //     const config = {
    //         headers: {
    //             Accept: "application/json"
    //         }
    //     };

    //     try {
    //         const response = await axios.get('https://icanhazdadjoke.com/search', config);
    //         this.jokes = response.data.results;
    //     } catch(error) {
    //         console.log(error);
    //     }
    // },
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