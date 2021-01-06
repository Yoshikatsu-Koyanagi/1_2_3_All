<template>
<div>
   <canvas ref="canv1" :width="width" :height="height"></canvas>
   <canvas ref="canv2" :width="width" :height="height"></canvas>
   <canvas ref="canv3" :width="width" :height="height"></canvas>
   <canvas ref="canvAll" :width="width" :height="height"></canvas>
</div>
</template>

<script>
export default { 
  props: ["width","height","bg_c_1","bg_c_2"],
  data() {
    return {
      num_width_ratio: 0.95,
      num_height_ratio: 0.95,
      flame_weight_ratio: 0.02, //キャンバスの横幅と高さの平均に対するボタンの枠の太さの割合
      font_ratio: 0.8, //数字ボタンの高さに対するフォントサイズの割合
      font_name: "meirio", //フォントの書体
      r_ratio: 0.1, //キャンバスの横幅と高さの平均に対する数字ボタンの枠の角の半径の割合
    }
  },
  methods: {
    draw_1_btn(num_color1){
      //数字ボタンの枠
      this.context1.globalCompositeOperation = "destination-out";
      this.context1.beginPath();
      this.context1.moveTo(this.num_side_margin+this.r,this.num_top_margin);
      this.context1.arc(this.num_side_margin+this.r, this.num_top_margin+this.r, this.r, Math.PI*1.5, Math.PI, true);  
      this.context1.lineTo(this.num_side_margin, this.num_top_margin+this.num_height-this.r);
      this.context1.arc(this.num_side_margin+this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI, Math.PI*0.5, true); 
      this.context1.lineTo(this.num_side_margin+this.num_width-this.r,this.num_top_margin+this.num_height);
      this.context1.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI*0.5, Math.PI*0, true); 
      this.context1.lineTo(this.num_side_margin+this.num_width,this.num_top_margin+this.r);
      this.context1.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.r, this.r, Math.PI*0, Math.PI*1.5, true); 
      this.context1.closePath();
      this.context1.fillStyle = "rgba(0,0,0,1)";
      this.context1.fill();

      this.context1.globalCompositeOperation = "source-over";
      this.context1.fillStyle = num_color1;
      this.context1.fill();

      //数字ボタンの"数字"
      this.context1.font = this.font;
      this.context1.fillStyle = "rgba(0,0,0,1)";
      this.context1.textAlign = "center";
      this.context1.fillText(1, this.nbw*0.5, this.num_top_margin+this.num_height*0.8,this.num_width);
    
      this.context1.lineWidth = this.flame_weight;	
      this.context1.strokeStyle = "rgb(0,0,0)"; 
      this.context1.stroke();
    },
    draw_2_btn(num_color2){
      //数字ボタンの枠
      this.context2.globalCompositeOperation = "destination-out";
      this.context2.beginPath();
      this.context2.moveTo(this.num_side_margin+this.r,this.num_top_margin);
      this.context2.arc(this.num_side_margin+this.r, this.num_top_margin+this.r, this.r, Math.PI*1.5, Math.PI, true);  
      this.context2.lineTo(this.num_side_margin, this.num_top_margin+this.num_height-this.r);
      this.context2.arc(this.num_side_margin+this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI, Math.PI*0.5, true); 
      this.context2.lineTo(this.num_side_margin+this.num_width-this.r,this.num_top_margin+this.num_height);
      this.context2.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI*0.5, Math.PI*0, true); 
      this.context2.lineTo(this.num_side_margin+this.num_width,this.num_top_margin+this.r);
      this.context2.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.r, this.r, Math.PI*0, Math.PI*1.5, true); 
      this.context2.closePath();
      this.context2.fillStyle = "rgba(0,0,0,1)";
      this.context2.fill();

      this.context2.globalCompositeOperation = "source-over";
      this.context2.fillStyle = num_color2;
      this.context2.fill();

      //数字ボタンの"数字"
      this.context2.font = this.font;
      this.context2.fillStyle = "rgba(0,0,0,1)";
      this.context2.textAlign = "center";
      this.context2.fillText(2, this.nbw*0.5, this.num_top_margin+this.num_height*0.8,this.num_width);
    
      this.context2.lineWidth = this.flame_weight;	
      this.context2.strokeStyle = "rgb(0,0,0)"; 
      this.context2.stroke();
    },
    draw_3_btn(num_color3){
      //数字ボタンの枠
      this.context3.globalCompositeOperation = "destination-out";
      this.context3.beginPath();
      this.context3.moveTo(this.num_side_margin+this.r,this.num_top_margin);
      this.context3.arc(this.num_side_margin+this.r, this.num_top_margin+this.r, this.r, Math.PI*1.5, Math.PI, true);  
      this.context3.lineTo(this.num_side_margin, this.num_top_margin+this.num_height-this.r);
      this.context3.arc(this.num_side_margin+this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI, Math.PI*0.5, true); 
      this.context3.lineTo(this.num_side_margin+this.num_width-this.r,this.num_top_margin+this.num_height);
      this.context3.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI*0.5, Math.PI*0, true); 
      this.context3.lineTo(this.num_side_margin+this.num_width,this.num_top_margin+this.r);
      this.context3.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.r, this.r, Math.PI*0, Math.PI*1.5, true); 
      this.context3.closePath();
      this.context3.fillStyle = "rgba(0,0,0,1)";
      this.context3.fill();

      this.context3.globalCompositeOperation = "source-over";
      this.context3.fillStyle = num_color3;
      this.context3.fill();

      //数字ボタンの"数字"
      this.context3.font = this.font;
      this.context3.fillStyle = "rgba(0,0,0,1)";
      this.context3.textAlign = "center";
      this.context3.fillText(3, this.nbw*0.5, this.num_top_margin+this.num_height*0.8,this.num_width);
    
      this.context3.lineWidth = this.flame_weight;	
      this.context3.strokeStyle = "rgb(0,0,0)"; 
      this.context3.stroke();
    },
    draw_All_btn(num_colorAll){
      //数字ボタンの枠
      this.contextAll.globalCompositeOperation = "destination-out";
      this.contextAll.beginPath();
      this.contextAll.moveTo(this.num_side_margin+this.r,this.num_top_margin);
      this.contextAll.arc(this.num_side_margin+this.r, this.num_top_margin+this.r, this.r, Math.PI*1.5, Math.PI, true);  
      this.contextAll.lineTo(this.num_side_margin, this.num_top_margin+this.num_height-this.r);
      this.contextAll.arc(this.num_side_margin+this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI, Math.PI*0.5, true); 
      this.contextAll.lineTo(this.num_side_margin+this.num_width-this.r,this.num_top_margin+this.num_height);
      this.contextAll.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.num_height-this.r, this.r, Math.PI*0.5, Math.PI*0, true); 
      this.contextAll.lineTo(this.num_side_margin+this.num_width,this.num_top_margin+this.r);
      this.contextAll.arc(this.num_side_margin+this.num_width-this.r, this.num_top_margin+this.r, this.r, Math.PI*0, Math.PI*1.5, true); 
      this.contextAll.closePath();
      this.contextAll.fillStyle = "rgba(0,0,0,1)";
      this.contextAll.fill();

      this.contextAll.globalCompositeOperation = "source-over";
      this.contextAll.fillStyle = num_colorAll;
      this.contextAll.fill();

      //数字ボタンの"数字"
      this.contextAll.font = this.font;
      this.contextAll.fillStyle = "rgba(0,0,0,1)";
      this.contextAll.textAlign = "center";
      this.contextAll.fillText("全", this.nbw*0.5, this.num_top_margin+this.num_height*0.8,this.num_width);
    
      this.contextAll.lineWidth = this.flame_weight;	
      this.contextAll.strokeStyle = "rgb(0,0,0)"; 
      this.contextAll.stroke();
    },
  },
  mounted() {
    this.nbw = this.width;
    this.nbh = this.height;

    this.flame_weight = (this.nbw+this.nbh)*0.5*this.flame_weight_ratio //ボタンの枠の太さ
    this.num_width = this.nbw*this.num_width_ratio;
    this.num_height = this.nbh*this.num_height_ratio;
    this.num_side_margin = this.nbw*(1-this.num_width_ratio)*0.5;
    this.num_top_margin = this.nbh*(1-this.num_height_ratio)*0.5;
    this.r = (this.nbw+this.nbh)*0.5*this.r_ratio;
   
    let canvas1 = this.$refs.canv1;
    this.context1 = canvas1.getContext('2d');
    let canvas2 = this.$refs.canv2;
    this.context2 = canvas2.getContext('2d');
    let canvas3 = this.$refs.canv3;
    this.context3 = canvas3.getContext('2d');
    let canvasAll = this.$refs.canvAll;
    this.contextAll = canvasAll.getContext('2d');

    if (this.bg_c_1 === undefined){
      this.bg1 = "rgba(20,49,237,0.1)";
    } 
    else {
      this.bg1 = this.bg_c_1;
    }
    if (this.bg_c_2 === undefined){
      this.bg2 = "rgba(20,49,237,0.15)";
    }
    else {
      this.bg2 = this.bg_c_2;
    }

    this.gradient1_b = this.context1.createLinearGradient(0, this.nbh*0.5, this.nbw, this.nbh*0.5);
    this.gradient1_b.addColorStop(0.0 , this.bg1);
    this.gradient1_b.addColorStop(1.0 , this.bg2);
    this.gradient2_b = this.context2.createLinearGradient(0, this.nbh*0.5, this.nbw, this.nbh*0.5);
    this.gradient2_b.addColorStop(0.0 , this.bg1);
    this.gradient2_b.addColorStop(1.0 , this.bg2);
    this.gradient3_b = this.context3.createLinearGradient(0, this.nbh*0.5, this.nbw, this.nbh*0.5);
    this.gradient3_b.addColorStop(0.0 , this.bg1);
    this.gradient3_b.addColorStop(1.0 , this.bg2);
    this.gradientAll_b = this.contextAll.createLinearGradient(0, this.nbh*0.5, this.nbw, this.nbh*0.5);
    this.gradientAll_b.addColorStop(0.0 , this.bg1);
    this.gradientAll_b.addColorStop(1.0 , this.bg2);
    this.context1.fillStyle = this.gradient1_b;
    this.context1.fillRect(0,0,this.nbw,this.nbh); 
    this.context2.fillStyle = this.gradient2_b;
    this.context2.fillRect(0,0,this.nbw,this.nbh);  
    this.context3.fillStyle = this.gradient3_b;
    this.context3.fillRect(0,0,this.nbw,this.nbh); 
    this.contextAll.fillStyle = this.gradientAll_b;
    this.contextAll.fillRect(0,0,this.nbw,this.nbh); 
    

    //数字ボタンを作成
    this.font_size = this.num_height*this.font_ratio; //フォントサイズ
    this.font = `${this.font_size}px ${this.font_name}`; //フォントサイズと書体    
    let num_color1; //数字ボタンの色
    let num_color2; //数字ボタンの色
    let num_color3; //数字ボタンの色
    let num_colorAll; //数字ボタンの色
    this.gradient1 = this.context1.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
    this.gradient1.addColorStop(0.0 , 'rgba(0,0,0,0.35)');
    this.gradient1.addColorStop(0.8 , 'rgba(0,0,0,0.05)');
    this.gradient2 = this.context2.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
    this.gradient2.addColorStop(0.0 , 'rgba(0,0,0,0.35)');
    this.gradient2.addColorStop(0.8 , 'rgba(0,0,0,0.05)');
    this.gradient3 = this.context3.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
    this.gradient3.addColorStop(0.0 , 'rgba(0,0,0,0.35)');
    this.gradient3.addColorStop(0.8 , 'rgba(0,0,0,0.05)');
    this.gradientAll = this.contextAll.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
    this.gradientAll.addColorStop(0.0 , 'rgba(0,0,0,0.35)');
    this.gradientAll.addColorStop(0.8 , 'rgba(0,0,0,0.05)');
    num_color1 = this.gradient1;
    num_color2 = this.gradient2;
    num_color3 = this.gradient3;
    num_colorAll = this.gradientAll;
    this.draw_1_btn(num_color1);
    this.draw_2_btn(num_color2);
    this.draw_3_btn(num_color3);
    this.draw_All_btn(num_colorAll);
    let num_down = false;
    let touch = false;   


    //タッチされたとき（スマホ）
    canvas1.addEventListener('touchstart', () => { 
        let gradient1_2 = this.context1.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradient1_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradient1_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_color1 = gradient1_2;
        this.draw_1_btn(num_color1);
        num_down = true;
        touch = true;
    },　{
      passive: true
    });

    //タッチが離れたとき（スマホ）
    canvas1.ontouchend = (e) => {
        num_color1 = this.gradient1;
        this.draw_1_btn(num_color1);  
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
        this.$emit("click1");
        num_down = false;
        touch = true;
        }
    }

    //クリックが押されたとき
    canvas1.onmousedown = (e) => {
      if (touch == false) {
        let gradient1_2 = this.context1.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradient1_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradient1_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_color1 = gradient1_2;
        this.draw_1_btn(num_color1);
        num_down = true;
      }
    }

    //クリックが離されたとき
    canvas1.onmouseup = (e) => {
      if (touch == false) {
        num_color1 = this.gradient1;
        this.draw_1_btn(num_color1); 
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
          this.$emit("click1");
          num_down = false;
        }
      }
    } 

    //マウスがキャンバス外に出た時
    canvas2.onmouseout = (e) => {
      if (touch == false) {
        num_color2 = this.gradient2;
        this.draw_2_btn(num_color2);
        num_down = false;
      }
    }   


    //タッチされたとき（スマホ）
    canvas2.addEventListener('touchstart', () => { 
        let gradient2_2 = this.context2.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradient2_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradient2_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_color2 = gradient2_2;
        this.draw_2_btn(num_color2);
        num_down = true;
        touch = true;
    },　{
      passive: true
    });

    //タッチが離れたとき（スマホ）
    canvas2.ontouchend = (e) => {
        num_color2 = this.gradient2;
        this.draw_2_btn(num_color2);  
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
        this.$emit("click2");
        num_down = false;
        touch = true;
        }
    }

    //クリックが押されたとき
    canvas2.onmousedown = (e) => {
      if (touch == false) {
        let gradient2_2 = this.context2.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradient2_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradient2_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_color2 = gradient2_2;
        this.draw_2_btn(num_color2);
        num_down = true;
      }
    }

    //クリックが離されたとき
    canvas2.onmouseup = (e) => {
      if (touch == false) {
        num_color2 = this.gradient2;
        this.draw_2_btn(num_color2); 
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
          this.$emit("click2");
          num_down = false;
        }
      }
    } 

    //マウスがキャンバス外に出た時
    canvas2.onmouseout = (e) => {
      if (touch == false) {
        num_color2 = this.gradient2;
        this.draw_2_btn(num_color2);
        num_down = false;
      }
    }


    //タッチされたとき（スマホ）
    canvas3.addEventListener('touchstart', () => { 
        let gradient3_2 = this.context3.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradient3_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradient3_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_color3 = gradient3_2;
        this.draw_3_btn(num_color3);
        num_down = true;
        touch = true;
    },　{
      passive: true
    });

    //タッチが離れたとき（スマホ）
    canvas3.ontouchend = (e) => {
        num_color3 = this.gradient3;
        this.draw_3_btn(num_color3);  
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
        this.$emit("click3");
        num_down = false;
        touch = true;
        }
    }

    //クリックが押されたとき
    canvas3.onmousedown = (e) => {
      if (touch == false) {
        let gradient3_2 = this.context3.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradient3_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradient3_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_color3 = gradient3_2;
        this.draw_3_btn(num_color3);
        num_down = true;
      }
    }

    //クリックが離されたとき
    canvas3.onmouseup = (e) => {
      if (touch == false) {
        num_color3 = this.gradient3;
        this.draw_3_btn(num_color3); 
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
          this.$emit("click3");
          num_down = false;
        }
      }
    } 

    //マウスがキャンバス外に出た時
    canvas3.onmouseout = (e) => {
      if (touch == false) {
        num_color3 = this.gradient3;
        this.draw_3_btn(num_color3);
        num_down = false;
      }
    }


    //タッチされたとき（スマホ）
    canvasAll.addEventListener('touchstart', () => { 
        let gradientAll_2 = this.contextAll.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradientAll_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradientAll_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_colorAll = gradientAll_2;
        this.draw_All_btn(num_colorAll);
        num_down = true;
        touch = true;
    },　{
      passive: true
    });

    //タッチが離れたとき（スマホ）
    canvasAll.ontouchend = (e) => {
        num_colorAll = this.gradientAll;
        this.draw_All_btn(num_colorAll);  
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
        this.$emit("clickall");
        num_down = false;
        touch = true;
        }
    }

    //クリックが押されたとき
    canvasAll.onmousedown = (e) => {
      if (touch == false) {
        let gradientAll_2 = this.contextAll.createLinearGradient(this.nbw*0.5,this.num_top_margin,this.nbw*0.5,this.num_top_margin+this.num_height);
        gradientAll_2.addColorStop(0.0 , 'rgba(0,0,0,0.5)');
        gradientAll_2.addColorStop(0.8 , 'rgba(0,0,0,0.3)');
        num_colorAll = gradientAll_2;
        this.draw_All_btn(num_colorAll);
        num_down = true;
      }
    }

    //クリックが離されたとき
    canvasAll.onmouseup = (e) => {
      if (touch == false) {
        num_colorAll = this.gradientAll;
        this.draw_All_btn(num_colorAll); 
        //数字ボタンが押されて且つ数字ボタン上で離されたとき        
        if (num_down == true) {
          this.$emit("clickall");
          num_down = false;
        }
      }
    } 

    //マウスがキャンバス外に出た時
    canvasAll.onmouseout = (e) => {
      if (touch == false) {
        num_colorAll = this.gradientAll;
        this.draw_All_btn(num_colorAll);
        num_down = false;
      }
    }
  },  
}
</script>