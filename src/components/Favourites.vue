<template>
  <div class="favority">
    <div class="ui-top">
      <div class="ui-top-companyname">Collectioon your favourites</div>

      <div class="search-wrapper">
        <img
          src="/assets/Icons/Search White.svg"
          alt="Search Icon"
          class="search-icon"
        />

        <input
          type="text"
          v-model="searchQuery"
          @input="searchMovies"
          placeholder="Search title and add to grid"
          class="search-input"
        />
      </div>
    </div>

    <hr class="favority-divider" />
    <div class="movie-grid">
      <div class="movie-card" v-for="(movie, index) in movies" :key="index">
        <img :src="movie.image" alt="Movie Poster" class="movie-image" />
        <h3>{{ movie.title }}</h3>
        <p class="movie-description" v-html="movie.description"></p>

        <button class="close-btn" @click="removeMovie(index)">
          <img
            src="/assets/Icons/Close White.svg"
            alt="Close"
            class="close-icon"
          />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      movies: [
        {
          title: "Batman Returns",
          description:
            "Lorem ipsum dolor sit amet,<br/>consetetur sadipscing elitr, sed diam<br/>nonumy eirmod tempor invidunt ut…",
          image: "/assets/Images/Batman.jpg",
        },
        {
          title: "Wild Wild West",
          description:
            "Lorem ipsum dolor sit amet,<br/>consetetur sadipscing elitr, sed diam<br/>nonumy eirmod tempor invidunt ut…",
          image: "/assets/Images/Wild West.jpg",
        },
        {
          title: "The Amazing Spiderman",
          description:
            "Lorem ipsum dolor sit amet,<br/>consetetur sadipscing elitr, sed diam<br/>nonumy eirmod tempor invidunt ut…",
          image: "/assets/Images/Spiderman.jpg",
        },
      ],
    };
  },
  methods: {
    async searchMovies() {
      if (this.searchQuery.trim() === "") return;

      try {
        const res = await fetch(
          `https://api.tvmaze.com/search/shows?q=${this.searchQuery}`
        );
        const data = await res.json();

        if (data.length > 0) {
          const show = data[0].show;
          const newMovie = {
            title: show.name,
            description:
              show.summary?.replace(/<[^>]+>/g, "") ||
              "No description available.",
            image:
              show.image?.medium ||
              "https://via.placeholder.com/210x295?text=No+Image",
          };

          const exists = this.movies.find(
            (movie) => movie.title === newMovie.title
          );
          if (!exists) {
            this.movies.push(newMovie);
          }

          this.searchQuery = "";
        }
      } catch (error) {
        console.error("Movie search failed:", error);
      }
    },
    removeMovie(index) {
      this.movies.splice(index, 1);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");
.favority {
  background: #151515;
  color: white;
  padding: 2rem 1.5rem 0.5rem;
  font-size: 0.9rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.ui-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.ui-top-companyname {
  font-family: "Trebuchet MS", sans-serif;
  font-size: 24.5px;
  font-weight: bold;
  color: white;
}

.search-wrapper {
  display: flex;
  align-items: center;
  background-color: #1e1e1e;
  border: 1px solid white;
  border-radius: 4px;
  padding: 0.3rem 0.6rem;
}

.search-icon {
  height: 16px;
  width: 16px;
  color: white;
  margin-right: 0.4rem;
  font-size: 1rem;
}

.search-input {
  font-family: "Lucida Sans Unicode", sans-serif;
  font-size: 12px;
  background-color: transparent;
  border: none;
  outline: none;
  color: white;
  width: 300px;
  caret-color: white;
}

.search-input::placeholder {
  color: #ccc;
}

.favority-divider {
  border: none;
  border-top: 2px solid white;
  margin: 0px;
}

.movie-library {
  padding: 1rem;
  background: #111;
  color: white;
}

.movie-grid-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.movie-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: space-between;
}

.movie-card {
  background-color: #1e1e1e;
  padding: 1rem;
  border-radius: 8px;
  position: relative;
  width: calc(33.33% - 1rem);
  padding: 2rem;
  text-align: left;
}

.movie-card h3 {
  font-family: "Trebuchet MS", sans-serif;
  font-size: 21.3px;
  font-weight: bold;
}

.movie-description {
  font-family: "Lucida Sans Unicode", sans-serif;
  font-size: 12px;
  line-height: 1.5;
  color: white; /* optional, to keep consistency */
}

.movie-image {
  width: 100%;
  height: 550px;
  object-fit: cover;
  border-radius: 0px;
  margin-bottom: 0.5rem;
}

.close-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: #363636ff;
  border: none;
  color: white;
  font-weight: bold;
  border-radius: 0;
  cursor: pointer;
  padding: 4px 8px;
}
@media (max-width: 600px) {
  .ui-top {
    flex-direction: column;
    align-items: flex-start;
  }

  .search-wrapper {
    width: 100%;
    max-width: 100%;
    margin-top: 0.5rem;
  }

  .search-input {
    font-size: 1rem;
  }

  .ui-top-companyname {
    font-size: 1.1rem;
  }
  @media (max-width: 768px) {
    .movie-card {
      width: calc(50% - 1rem);
    }
  }

  @media (max-width: 480px) {
    .movie-card {
      width: 100%;
    }
  }
}
</style>
