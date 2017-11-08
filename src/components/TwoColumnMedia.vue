<template>
  <div class="hero">
    <section class="featured-album">
      <div class="featured-album__items">
        <div class="download-album">
          <div class="download-album-cover">
            <a :href="blok.left_media_url">
              <img class="album-cover" :src="blok.left_media" :alt="blok.left_media_title">
            </a>
          </div>
        </div>
        <div class="music-embed" v-html="musicEmbed">
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import marked from 'marked'

export default {
  props: ['blok'],
  data () {
    return {
      musicEmbed: marked(this.blok.music_embed)
    }
  }
}
</script>

<style lang="scss" scoped>
  .featured-album {
    text-align: center;
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .featured-album__items {
    display: flex;
    flex-direction: column-reverse;

    @media (min-width: 700px) {
      flex-direction: row;
      justify-content: space-evenly;
    }

    img {
      width: 100%
    }

    @media (min-width: 700px) {
      img {
        height: 90%;
        width: auto;
      }
    }

  }

  button {
    width: 40%;
    display: inline-block;
    height: 38px;
    padding: 0 30px;
    color: black;
    text-align: center;
    font-size: 11px;
    font-weight: 600;
    line-height: 38px;
    letter-spacing: .1rem;
    text-transform: uppercase;
    text-decoration: none;
    white-space: nowrap;
    background-color: #EBC967;
    border-radius: 4px;
    border: 1px solid #bbb;
    cursor: pointer;
    box-sizing: border-box;
  }

  button:hover, button:focus {
    color: #333;
    border-color: #888;
    outline: 0;
  }

  @media (min-width: 700px) {
    button {
      width: 60%;
    }
  }

   @media (min-width: 750px) {
    .soundcloud-widget {
      width: 50%;
      margin: 0;
    }
    iframe {

    }
  }
</style>
