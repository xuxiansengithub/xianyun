<template>
  <div>
    <Header/>
    <nuxt />
    <Footer/>
  </div>
</template>

<script>
import Header from '@/components/header.vue'
import Footer from '@/components/footer.vue'
export default {
  components:{
    Header,
    Footer
  }
}
</script>

<style lang='less'>
  *{
    margin:0;
    padding:0;
  }
  ul,li,ol{
    list-style: none;
  }
  a{
    text-decoration: none;
    color:black;
  }
  em,i{
    font-style:normal;
  }
</style>
