<template>
  <div class="title">
     <w-cates :cates="cates" @getCatId="getCatId"></w-cates>
     <w-articles :articles="articles" @getArtId="getArtIds"></w-articles>
  </div>
</template>

<script>
import { get,getNoParam } from "@/utils/request.js";
import wCates from "./components/w-cates.vue"
import wArticles from "./components/w-articles.vue"
export default {
  name: 'App',
  data() {
    return {
      cates: [],
      articles: [],
    };
  },
   async created() {
    //加载

    let res1 = await getNoParam("api/articlecate/getmobilearticlecates");
    this.cates = res1.data;

    let res2 = await getNoParam("/api/articles/open");
    this.articles = res2.data;
  },
  methods: {
   async getCatId(catId) {
     let that=this;
      console.log(catId);
      let params={cat_id:catId}
      let res=await get('api/articles/open',params)
      console.log(res);
      that.articles=res.data;
    },
    async getArtIds(ArtId){
      console.log(ArtId);
      let params={id:ArtId};
      let res=await get('api/article/one',params);
      let artlink=res.data.link;
      console.log(artlink);
      // this.$router.push({url:"artlink"});
      window.location.href = artlink;
    }
  },
  components: {
    wCates, 
    wArticles,
  }
}
</script>

<style>

</style>
