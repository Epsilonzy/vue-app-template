<template>
    <div class="hello">
      <h2>这是一个为移动端适配好的vue模板，直接从git clone即可用</h2>
      <h2>别忘了先安装依赖，npm install</h2>
      <h2>它集成了node-sass,sass-loader,vue-scroller,px2rem,rem,axios等适合移动端开发的依赖</h2>
      <button @click="test()">axios测试</button>
    </div>
</template>

<script>
  export default {
      name: 'HelloWorld',
      data () {
        return {
         
        }
      },
      methods:{
        test(){
          this.$axios.get('http://localhost:3000').then(res=>{
            console.log(res.data);
          })
        }
      }
  }
</script>
<style lang="scss" scoped>
.hello{
    h1,h2{
    font-weight: normal;
    font-size:16px;
  }
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
