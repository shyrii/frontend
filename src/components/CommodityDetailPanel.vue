<template>
    <div class="wrapper">
    <div class="mask" @click="close"></div>
    <div class="content">
      <div class="img_detail">
        <div class="img">
          <img src="../assets/commodity.jpg" style="width: 600px;height: 600px;margin-top: 40px;margin-left: 40px;"/>

          <div class="four_imgs_box">
            <img src="../assets/left2.svg" @click="handleLeft" style=" width:50px; height:100px;margin-top:5%;"/>
            <img src="../assets/right2.svg" @click="handleRight" style=" width:50px; height:100px; margin-left:84.5%; "/>
            <div class="four_imgs">
                <div class="one_img" v-for="i in 4" :key="i">
                  <img src="../assets/commodity.jpg" style="width:120px;height:130px;"/>                           
                </div>
            </div>
              
          </div>
          
        </div>
              

        <div class="detail">
          <hr style="margin-top:20%;margin-left:3%;height:3px;width:500px;border:0px;background-color:#ff8d1a;color:ff8d1a;"/>
          <hr style="margin-top:-10%;margin-left:5%;height:500px;width:2px;border:0px;background-color:#ffc300;color:ffc300;"/>
          <div class="name">
              <h1 style="font-size:45px;">商品名称如果很长的话会占两行</h1>
          </div>
          <hr size="3" style="margin-top:-2%;margin-left:30%;color:#ffc300;border-style:dashed ;width:380px;"/>
          <p style="margin-top:1%;margin-left:12%;color:#505050;font-size:25px;" >售价:</p>
          <strong><h1 style="margin-top:-5%;margin-left:25%;color:#ff8d1a;font-size:60px;">{{price}}</h1></strong>
          <p style="margin-top:-5%;margin-left:12%;color:#505050;font-size:25px;">库存: {{inventory}} 件</p>
          <p style="margin-top:-2%;margin-left:12%;color:#505050;font-size:25px;">销量: {{sales_number}} 件</p>
          <div>
              <p style="margin-left:12%;color:#505050;font-size:25px;">数量:</p>
              <div class="changeNum">
                  <img src="../assets/left1.svg" @click="handleReduce" style=" width:50px; height:40px;margin-left:-5%;"/>
                  <img src="../assets/right1.svg" @click="handleAdd" style=" width:50px; height:40px;margin-left:38%;"/>  
                  <div class="buyNum">
                      <p style="font-size:25px;color:#505050;">{{ buy_number}}</p>
                  </div>
                                    
              </div>
          </div>

          <div class="buttons" >
              <div class="button1" @click="buyItNow" >
                  <h2 style="color:#ffffff;font-size:25px;border-top:20%;" >立即购买</h2>
              </div>

              <div class="button2" @click="addToCart">
                  <h2 style="color:#ffffff;font-size:25px;">加入购物车</h2>
              </div>
          </div>
          </div>
      </div>

      <div class="text">
          <div class="title">
              <h1 style="color:#383838;font-size:35px;text-align:center; " >商品详情</h1>
          </div>
          <div class="paragraph">
              <p>{{descripion}}</p>                  
          </div>
        </div>
      </div>
      
    </div>
</template>



<script>
export default {
  name: "CommodityDetail",
  props: ["goods_id"],
  data() {
    return {
      price: "RMB 180.00",
      inventory: 5,
      sales_number: 10,
      buy_number: 0,
      descripion:
        "  多肉植物（succulent plant）是指植物的根、茎、叶三种营养器官中至少有一种是肥厚多汁并且具备储藏大量水分功能的植物。其至少具有一种肉质组织，这种组织是一种活组织，除其他功能外，它能储藏可利用的水，在土壤含水状况恶化、植物根系不能再从土壤中吸收和提供必要的水分时，它能使植物暂时脱离外界水分供应而独立生存。 [1]  据粗略统计，全世界共有多肉植物一万余种，在分类上隶属100余科。" +
        "\n" +
        "  多肉植物（包括仙人掌类）中有不少种类具药用成分。例如，人们会选用刺少肉厚的仙人掌属植物茎片去皮捣烂后外敷,能治痈疖等皮肤病，该属中的金武扇和宝剑掌也对腮腺炎有明显的疗效。一种球形仙人掌——乌羽玉的茎和粗大肉质根都含有一种称为墨斯卡灵的生物碱，具致幻麻醉作用。墨西哥的印第安人在举行宗教仪式时，常边喝用龙舌兰酿制的蒲儿甘酒，边食用乌羽玉（当地人称为‘peyote’）在这种彻夜狂欢中，乌羽玉的消耗非常惊人。他们似乎也很懂得保护资源，在采集这种植物时从不连根挖而是用刀贴地割取，这样土中的肉质根能很快长出新的球茎。另有两种稀有的观赏植物：月世界和岩牡丹属植物，因含同样的成分而被当做代用品。"
    };
  },
  methods: {
    handleReduce: function() {
      if (this.buy_number > 0) this.buy_number--;
    },
    handleAdd: function() {
      if (this.inventory > this.buy_number) this.buy_number++;
    },
    buyItNow: function() {
      console.log("立即购买");
      this.$router.push({
        path: "/performOrder"
      });
    },
    addToCart: function() {
      console.log("加入购物车");
       this.$router.push({
        path: "/cart"
      });
    },
    handleLeft: function() {
      console.log("left");
    },
    handleRight: function() {
      console.log("right");
    },
    close() {
      this.$emit('close')
    }
  }
};
</script>



<style scoped>
.wrapper {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

.wrapper > .mask {
  height: 100vh;
  width: 100vw;
  background-color: rgba(0, 0, 0, 0.5);
  animation: fadeIn 0.5s ease 1 backwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideIn {
  from {
    transform: translateX(100%)
  }
  to {
    transform: translateX(0%)
  }
}

.content {
  position: absolute;
  overflow-y: auto;
  right: 0px;
  top: 0px;
  width: 70vw;
  height: 100vh;
  background-color: white;
  animation: slideIn 0.5s ease 1 backwards;
}

.img_detail {
  display: inline;
}

.img {
  display: inline-block;
  vertical-align: top;
}

.four_imgs_box {
  background-color: #ffc300;
  width: 655px;
  height: 160px;
  margin-left: 2%;
  margin-top: 2%;
}

.four_imgs {
  width: 560px;
  height: 150px;
  background-color: white;
  position: absolute;
  display: flex;
  justify-content: space-around;
  margin-top: -8.7%;
  margin-left: 3.2%;
  text-align: center;
}

.one_img {
  width: 130px;
  height: 130px;
  margin-top: 2%;
}

.detail {
  display: inline-block;
  vertical-align: top;
}

.name {
  margin-top: -95%;
  margin-left: 10%;
  width: 450px;
}

.changeNum {
  background-color: #ffc300;
  width: 150px;
  height: 40px;
  margin-left: 27%;
  margin-top: -12%;
}

.buyNum {
  width: 80px;
  height: 35px;
  background-color: white;
  text-align: center;
  margin-top: -44%;
  margin-left: 20%;
}

.buttons {
  margin-top: 11%;
  margin-left: 22%;
  text-align: center;
}

.button1 {
  background-color: #ff8d1a;
  width: 320px;
  height: 60px;
  background-image: "../assets/buyIt.svg";
}

.button2 {
  background-color: #ff8d1a;
  width: 320px;
  height: 60px;
}

.text {
  width: 100%;
}

.title {
  width: 30%;
  height: 70px;
  background-color: #e5e5e5;
  margin-left: 70%;
  margin-top: -5%;
  border-radius: 20px 20px 0 0;
}

.paragraph {
  width: 100%;
  background-color: #e5e5e5;
  margin-top: -1.3%;
}
</style>
