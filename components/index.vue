<template>
  <section class="container">
    <div>
      <h3> {{tagname}}のタグがつけられた投稿の一覧</h3>
      <div>
        <input type='text' @keypress.enter="tagsearch" v-model='tagname'>
        <button @click="tagsearch">検索</button>
      </div>
      <ul>
        <li v-for="item in items" :key="item.id">
          <h4>
            <span>{{item.title}}</span>
            <small>
              <span>by</span>
              <nuxt-link :to="`/users/${item.user.id}`">
                {{item.user.id}}
              </nuxt-link>
            </small>
          </h4>
          <div>{{item.body.slice(0,130)}}......</div>
          <p><a target="_blank" :href="item.url">{{item.url}}</a></p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>

export default {
    async asyncData({ app }){
        const tagname = 'nuxt.js'
        const items = await app.$axios.$get(`https://qiita.com/api/v2/items?query=tag:${tagname}`)
        return {
            items
        }
    },
    data(){
      return {tagname : 'nuxt.js', items: ''}
    },
    methods: {
      async tagsearch() {
        this.items = await this.$axios.$get(`https://qiita.com/api/v2/items?query=tag:${this.tagname}`);
      }
    }
}
</script>

<style>
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

h3 {
  margin:16px 0;
  padding: 8px 0;
  border-bottom: solid 1px#e5e5e5;
}

li + li {
  margin: 16px 0;
}

p {
  margin: 8px;
}

</style>

