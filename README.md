# 1_2_3_All

----index.html----
````
<div id="App">
      <mycomp
      :width = 500
      :height = 300
      :bg_c_1 = bg_c_1                      //背景の端の色 (書かなければデフォルト:"rgba(20,49,237,0.1)")
      :bg_c_2 = bg_c_2                      //背景の端と中央の間の色 (書かなければデフォルト:"rgba(20,49,237,0.15)")
      :bg_c_3 = bg_c_3                      //背景の中央の色 (書かなければデフォルト:"rgba(20,49,237,0.3)")
      @click1="click1"                      //@click1: ボタンが押されたらclick1()発火
      @click2="click2"                      //@click2: ボタンが押されたらclick2()発火
      @click3="click3"                      //@click3: ボタンが押されたらclick3()発火
      @clickall="clickall"></mycomp>        //@clickall: ボタンが押されたらclickall()発火
</div>
  ````
  
  ----index.js----
  ````
import Vue from 'vue';
import component1_2_3_All from '1_2_3_All';

new Vue({
    el: '#App',
    data: {
         bg_c_1: "rgba(100,99,255,0.05)",       
         bg_c_2: "rgba(100,99,255,0.125)",      
         bg_c_3: "rgba(100,99,255,0.25)",       
    },
    components: {
        'mycomp': component1_2_3_All,
    },　
    methods: {
        click1(){
            console.log("1")
        },
        click2(){
            console.log("2")
        },
        click3(){
            console.log("3")
        },
        clickall(){
            console.log("All")
        },
    }
})
````
