<template>
  <div class="maindiv">
    <!-- クリックはv-on:click="関数名" -->
    <button class="cent" v-on:click="fetchfnc">注文状況表示</button>
    <div>
      <a> id </a>
      <a>:mail</a>
      <a>: tell</a>
      <a>: name</a>
      <a>: address</a>
      <a>: ordertime</a>
    </div>

    <!-- v-forでループさせてタグを表示させる。 -->
    <div v-for="j_loop in json_arr" :key="j_loop.id">
      <!-- ListComponentsに取得したJsonデータをそれぞれPropsに入れて渡す。 -->
      <ListComponents
        :id_props="j_loop.id"
        :name_props="j_loop.name"
        :mail_props="j_loop.mail"
        :tell_props="j_loop.tel"
        :address_props="j_loop.address"
        :time_props="j_loop.ordertime"
      ></ListComponents>
    </div>
  </div>
</template>


<script>
/* eslint-disable*/
// 準備しておいたリストの１行の中身になる下位のコンポーネントをインポートする
import ListC from "./ListComponent.vue";

// エクスポートすることで<template>のタグ構造が使用できる
export default {
  name: "test",
  components: {
    // ListComponentsコンポーネントとして使用できるようにする
    ListComponents: ListC,
  },
  // data関数内で変数（State?）宣言を行う
  data() {
    // return内に変数と初期値を入れる
    return {
      //  注文数のJsonを保存するための配列
      json_arr: {},
    };
  },
  // Methods内に使用する関数を作成しておく
  methods: {
    // 関数名：関数内容
    fetchfnc: function () {
      fetch("http://localhost:4000/showorder")
        .then((response) => {
          var t = response.json();
          console.log(t);
          return t;
        })
        .then((data) => {
          var r = data;
          console.log(r);
          // 結果を変数に保存。this.変数名にすること
          this.json_arr = r;
        });
    },
  },
};
</script>>

<style scoped>
.maindiv {
  /* float:left; */
  text-align: left;
}

.cent {
  margin-left: 30%;
  margin-right: 10%;
  margin-bottom: 20px;
  /* position:block; */
}
</style>