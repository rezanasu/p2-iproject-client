<template>
    <section id="main-content">
        <div class="container mt-5">
            <h1>DISCOVER PHOTOS</h1>
            <hr class="mt-3">
            <div class="row">
                <ImageCard
                v-for="pic in images"
                :key="pic.id"
                :picture="pic"
                >
                </ImageCard>

            </div>
        </div>
    </section>
</template>

<script>
import ImageCard from '../components/ImageCard'
export default {
  name: 'Home',
  components: {
    ImageCard
  },
  computed: {
    images () {
      return this.$store.state.images
    }
  },
  created () {
    this.$store.dispatch('fetchImages')
    this.$store.commit('setPage', 'Home')
  }
}
</script>

<style scoped>
/* DEMO GENERAL ============================== */
.hover {
    overflow: hidden;
    position: relative;
    padding-bottom: 60%;
  }

  .hover-overlay {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 90;
    transition: all 0.4s;
  }

  .hover img {
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    transition: all 0.3s;
  }

  .hover-content {
    position: relative;
    z-index: 99;
  }

  /* DEMO 1 ============================== */
  .hover-1 img {
    width: 105%;
    position: absolute;
    top: 0;
    left: -5%;
    transition: all 0.3s;
  }

  .hover-1-content {
    position: absolute;
    bottom: 0;
    left: 0;
    z-index: 99;
    transition: all 0.4s;
  }

  .hover-1 .hover-overlay {
    background: rgba(0, 0, 0, 0.5);
  }

  .hover-1-description {
    transform: translateY(0.5rem);
    transition: all 0.4s;
    opacity: 0;
  }

  .hover-1:hover .hover-1-content {
    bottom: 2rem;
  }

  .hover-1:hover .hover-1-description {
    opacity: 1;
    transform: none;
  }

  .hover-1:hover img {
    left: 0;
  }

  .hover-1:hover .hover-overlay {
    opacity: 0;
  }

  /* DEMO 2 ============================== */
.hover-2 .hover-overlay {
    background: linear-gradient(to top, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.1));
  }

  .hover-2-title {
    position: absolute;
    top: 50%;
    left: 0;
    text-align: center;
    opacity: 0;
    width: 100%;
    z-index: 99;
    transition: all 0.3s;
  }

  .hover-2-description {
    width: 30%;
    position: absolute;
    bottom: 0;
    opacity: 0;
    left: 70%;
    text-align: center;
    z-index: 99;
    transition: all 0.3s;
  }

  .hover-2:hover .hover-2-title {
    transform: translateY(-1.5rem);
    opacity: 1;
  }

  .hover-2:hover .hover-2-description {
    bottom: 0.5rem;
    opacity: 1;
  }

  .hover-2:hover .hover-overlay {
    background: linear-gradient(to top, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.1));
  }
</style>
