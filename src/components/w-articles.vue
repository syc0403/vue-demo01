<template>
  <div class="articles">
    <div class="article" v-for="article in articles" :key="article.article_id">
      <div class="article-img" v-if="article.thumb">
        <img :src="article - thumb" fit="cover" />
      </div>
      <div class="article-title" @click="sendArtId(article.article_id)">
        {{ article.title }}
      </div>
      <div class="article-author">
        {{ article.author }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    articles: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      articleData: this.articles,
      ArtId:""
    };
  },
  created() {
    console.log("-------------------------------------");
    console.log(this.articles);
  },
  watch: {
    articles: function (val) {
      this.articleData = val;
    },
  },
  methods: {
    sendArtId(ArtId) {
      var that = this;
      console.log(ArtId)
      that.$emit("getArtId", ArtId);
    },
  },
};
</script>
<style>
.article-img {
  width: 100px;
  height: 100px;
  float: left;
}
.articles {
  display: flex;
  flex-direction: column;
  font-size: 25px;
}
.article :hover {
  color: blue;
}
div.article-author {
  font-size: 15px;
  padding: 10px;
}
</style>