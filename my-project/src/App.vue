<template>
  <div id="app">
    <!--logo title-->
    <div class="header">
      <h1 class="title">商品管理</h1>

    </div>

    <!--输入部分input-->
    <div  class="form-warp">
      <div class="title">新增商品</div>
      <div class="content">

        名稱：<input type="text" placeholder=""  v-model="goods.name"/><br />
        價格：<input type="text" placeholder=""  v-model="goods.price"/><br />
        數量：<input type="text" placeholder="" v-model="goods.num"/><br />

      </div>
      <div class="form-btn">
        <button @click="addGoods">新增</button>
        <button @click="goods= { } ">清除</button>



      </div>

    </div>
    <!--显示表格-->
    <div class="table-warp">
      <div class="title">商品列表</div>
      <table border="1" align="center">

        <tr>
          <th>編號</th>
          <th>名稱</th>
          <th>價格</th>
          <th>數量</th>
          <th>刪除</th>
        </tr>
        <tr v-for="(item,index) in goodsArry" :key="item.id" @click="deleteGoods(index)">
          <td>{{index}}</td>
          <td>{{item.name}}</td>
          <td>{{item.price}}</td>
          <td>{{item.num}}</td>
          <td><button>刪除</button></td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data: function () {
      return {
        goods: {
          name: '',
          price: '',
          num: '',
        },
        goodsArry: [
          {name: '誠實豆沙包', price: 666, num: 10},
          {name: '謊言棒棒糖', price: 999, num: 20},
          {name: '大俠漢寶寶', price: 8787, num: 30}
        ]
      }
    },

    methods:{
      addGoods(){
        this.goodsArry.push(this.goods);
        this.goods={};
      },
      deleteGoods:function(index){
        this.goodsArry.splice(index,1);
      }

    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
