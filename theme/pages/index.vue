<template>
  <section class="section">
    <div class="columns is-mobile">

      <card
        title="Free"
        icon="github-circle"
      >
        Open source on <a href="https://github.com/buefy/buefy"> GitHub</a>
      </card>

      <card
        title="Responsive"
        icon="cellphone-link"
      >
        <b class="has-text-grey">Every</b> component is responsive
      </card>

      <card
        title="Modern"
        icon="alert-decagram"
      >
        Built with <a href="https://vuejs.org/">Vue.js</a> and <a href="http://bulma.io/">Bulma</a>
      </card>

      <card
        title="Lightweight"
        icon="arrange-bring-to-front"
      >
        No other internal dependency
      </card>
    </div>
    <div class="columns">
      <div v-for="(item, index) in works" :key=index>
        <p>{{item.title_display ? item.title_display : item.title}}</p>
        <p>
          <img :src="require(`~~/contents/${item.title}.png`)" alt="">
        </p>
        <p v-html="$md.render(item.caption)"></p>
        <p v-if="item.url">
          関連リンク
          <a :href="item.url">{{item.url}}</a>
        </p>
      </div>
    </div>
  </section>
</template>

<style>
  .columns {
    white-space: pre-wrap;
    word-wrap: break-word;
  }
</style>

<script lang="ts">
import Card from '~/components/Card.vue'

export default {
  name: 'HomePage',

  components: {
    Card
  },

  async asyncData () {
    return {
      works: (await import("~~/contents/works.yml")).default
    }
  }
}
</script>
