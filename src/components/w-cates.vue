<template>
<div>
    <div class="cates">
      <div v-for="cate in cates" :key="cate.cat_id">
        <div class="cate" v-if="cate.show_in_nav==1" @click="sendCatId(cate.cat_id)">{{cate.cat_name}}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
    props:{
        cates:{
            type:Array,
            required:true
        },
        
   } ,
   data() {
    return {
     
    };
  },
  methods:{
    sendCatId(catId){
       this.$emit("getCatId",catId);
    }
  }
}
</script>

<style>
.cates{
    white-space:nowrap;
    padding: 20px;
    text-align: center;
    font-size:20px;
    display: flex;

    }
.cate{
    display:inline;
    line-height:45px;
    padding: 0 20px;
}
.cate:hover{
    color:blue;
    }
</style>