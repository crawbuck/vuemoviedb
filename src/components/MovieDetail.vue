<template>
	<transition name="fade">
		<div class="movie-wrapper" :style="styles">
			<div class="movie-info">
				<h1>{{ movie.title }}</h1>
				<h3>Release Date: {{ movie.release_date }}</h3>
				<p>{{ movie.overview }}</p>
			</div>
		</div>
	</transition>
</template>

<script>
const backdropPath = "http://image.tmdb.org/t/p/original";
export default {
  name: 'MovieDetail',
	computed: {
		styles() {
			return {
				background: `url(${backdropPath}/${this.movie.backdrop_path}) no-repeat`
			}
		}
	},
	beforeCreate() {
		console.log('before create')
	},
	created: function() {
		console.log('created');
		this.fetchData();
	},	
	beforeMount() {
		console.log('before mount')
	},
	mounted() {
		console.log('mounted');
	},
	updated() {
		console.log('updated');
	},
	methods: {
		fetchData: async function() {
			try {
				const res = await fetch(
					`https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=a801043160624e00167982916b8047c5`  
				);
				const movie = await res.json();
				this.movie = movie;
			} catch(e) {
				console.log(e);
			}
		}
	},
	data() {
		return {
			movie: {} 
		};
	}	
};
</script>

<style lang="css" scoped>
	.movie-wrapper {
		position: relative;
		padding-top: 50vh;
		background-size: cover;
	}
	.movie-info {
		background-color: white;
		color: #222;
		padding: 2rem 10%;
	}
  .fade-enter-active, .fade-leave-active {
      transition: all 0.3s ease;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
    transform: translateY(100%);
  }	
</style>
