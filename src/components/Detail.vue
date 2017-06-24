<template>
    <div id="detail">
        <movie-item v-bind:movie="movie">
            <div class="movie-details">
                <p class="movie-genre">{{ movie.Genre }}</p>
                <p class="movie-plot">{{ movie.Plot }}</p>
                <table>
                    <tr>
                        <td>Released date: </td>
                        {{ movie.Released }}
                    </tr>
                    <tr>
                        <td>Running time: </td>
                        {{ movie.Runtime }}
                    </tr>
                    <tr>
                        <td>Director: </td>
                        {{ movie.Director }}
                    </tr>
                    <tr>
                        <td>Cast: </td>
                        {{ movie.Actors }}
                    </tr>
                </table>
            </div>
        </movie-item>
        <div class="home">
            <router-link v-bind:to="{ name: 'home' }">Back to results</router-link>
        </div>
    </div>
</template>

<script>
import MovieItem from './MovieItem.vue';

export default {
    props: ['movies'],
    computed: {
        movie() {
            let movie = this.movies.find(movie => movie.id === this.$route.params.id);
            return movie ? movie.movie : null;
        }
    },

    components: {
        MovieItem
    }
}
</script>

