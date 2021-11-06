<template>
  <!-- <ListComp class="lscmp"> -->
  <!-- クラス名など属性系に変数を当てる場合はv-bind:を使用する -->
  <div v-bind:class="style_coler">
    <!-- liタグにそれぞれPropsで渡された内容を表示させる・変数やPropsは{{変数名}} で使用する-->
    <div class="ord" v-bind:id="style_coler + id_props" >
      <!-- ボタン押下でフラグを変更しクラスとボタンの表記を変更 -->
      
      <div v-bind:class="style_coler +name_props">
        <button name="btn"  v-bind:class="name +  id_props" v-on:click="testfnc">{{ btntext }}</button>
      <span v-bind:class="name +  id_props">{{ id_props }}- </span>
      <span v-bind:class="name +  id_props">{{ name_props }} - </span>
      <span v-bind:class="name +  id_props"> {{ mail_props }} - </span>
      <span v-bind:class="name +  id_props"> {{ tell_props }} - </span>
      <span v-bind:class="name +  id_props">{{ address_props }} - </span>
      <span v-bind:class="name +  id_props">{{ time_props }}</span>
      </div>
      <div v-if="flg" class="pop" >
        <div class="info">
        <button v-on:click="testfnc">close</button>
        
        <p>注文詳細</p>
        </div>
        <div class="detailinfo">
        <p>注文ID: {{pop_text[0]}}</p>
        <p>メール：{{pop_text[1]}}</p>
        <p>電話番号：　{{pop_text[2]}}</p>
        <p>住所：　{{pop_text[3]}}</p>
        <p>注文者名：　{{pop_text[4]}}</p>
        <p>受付時刻：　{{pop_text[5]}}</p>
        </div>
        </div>
    </div>
  </div>
  <!-- </ListComp> -->
</template>


<script>
/* eslint-disable*/
// エクスポートすることで<template>のタグ構造が使用できる
export default {
  name: "list_test",
  // Propsをここで設定
  // Props名：型
  props: {
    id_props: String,
    name_props: String,
    mail_props: String,
    address_props: String,
    tell_props: String,
    time_props: String,
  },
  // data関数内で変数（State?）宣言
  data() {
    return {
      flg: false, //チェックのフラグ
      style_coler: "no-mk", //スタイルのクラス名
      btntext: "□", //ボタンのテキスト
      name: "class_record_",
      pop_text: [],
    };
  },
  methods: {
    // スイッチング用の関数
    testfnc: function (event) {
      var tmp = this.flg;
      var c = this.style_coler;
      var ele;
      var classname;
      var arr = [];

      console.log("flg" + ":" + tmp + " => " + !tmp);
      console.log("style" + ":" + c + " => " + this.style_coler);

      classname = event.target.className;
      ele = document.getElementsByClassName(classname);

      console.log("classname:" + classname);
      console.log(ele);
      // console.log(ele[1].textContent);

      for (const i of ele) {
        console.log(i.name);
        console.log(i.textContent);
        if (i.name !== "btn") {
          arr.push(i.textContent);
        }
      }

      console.log(arr);

      // フラグを逆転
      this.flg = !tmp;

      // フラグに応じて内容を変更
      if (this.flg) {
        this.style_coler = "mk";
        this.btntext = "☑︎";
        this.pop_text = arr;
      } else {
        this.style_coler = "no-mk";
        this.btntext = "□";
        this.pop_text = {};
      }
    },

    funconClick: function (event) {
      console.log(event.target);
    },
  },
};
</script>>
<style >
/* スタイルの内容 */
/* マークありの時に色を付ける */
.mk {
  background-color: pink;
}

.lscmp {
  /* float: left; */
  /* margin: auto; */
  margin-left: 0;
}

.ord {
  clear: both;
}

.pop {
  top: 5%;
  left: 10%;
  right: 10%;
  bottom: 5%;
  padding: 0px;
  background-color: lightblue;
  position: fixed;
  z-index: 1020;
  padding-left: 10px;
  border: solid;
  /* opacity: 0.9; */
}

.info p {
  background-color: white;
  margin: 10px;
  clear: both;
}

.info button {
  background-color: white;
  margin-right: 10px;
  float: right;
}

.detailinfo {
  /* float: left; */
  /* background-color:red;  */
  padding-left: 0;
  text-align: left;
  /* border: solid; */
}
</style>>