<template>

  <div>
    <el-carousel trigger="click" :height="bannerh"  @change="loadAnimate">
      <el-carousel-item v-for="(item,index) in sliderList" :key="index">
        <figure>
          <img :src="'../../static/img/slider/'+item.img" width="100%" alt="高端西服定制"/>
          <!--轮播图跳出文字
          <figcaption>
            <h1 :class="{ bounceInDown:slider_index==index }">{{ item.title }}</h1><br>
            <p :class="{ fadeInUp:slider_index==index }">{{ item.abstract }}</p><br>
            <router-link :to="item.link">
              <el-button class="slider-button" round :class="{ fadeInUp:slider_index==index }" >了解详情 >></el-button>
            </router-link>
          </figcaption>-->
        </figure>
      </el-carousel-item>
    </el-carousel>

    <ul class="home-kind">
      <li v-for="(item,index) in kind" :key="index">
        <h3>{{ item.title }}
          <div></div>
        </h3>
        <p>{{ item.info }}</p>
      </li>
    </ul>

    <el-container>
      <el-main>
        <!-- 品类 --->
        <div class="home-service">
          <h1>精选高端面料，特约行业资深设计师</h1>
          <p>客户涵盖国内多家百强企业，值得信赖</p>

          <el-row>
            <el-col :span="24">
              <ul>
                <li v-for="(item,index) in services" :key="index">
                  <div class="product-box">
                    <img :src="`../../../static/img/services/${index+1}.png`">
                    <div class="product-info">
                      <p class="product-title">{{ item.title }}</p>
                      <br/>
                      <p class="product-content">{{ item.info }}</p>
                    </div>
                  </div>
                </li>
              </ul>
            </el-col>
          </el-row>

        </div>
        <!-- 品类 end-->

        <!--news start-->
        <br/><br/>
        <el-row>
          <el-col :span="6" :offset="6">
           <h2>行业知识</h2>
          </el-col>
          <el-col :span="6">
           <h2>新闻动态</h2>
          </el-col>
        </el-row>

        <el-row type="flex" justify="start" class="news-content">
          <el-col :span="6" :offset="6" :pull="2" style="height: 4em; ">
            <div style="display: inline-block; vertical-align:middle">
              <ul>
                <li>
                  <div class="in-line" style="display: inline-block; vertical-align:middle; margin-bottom: -1.5em">
                    <div class="time" style="display: inline-block; vertical-align:middle">
                      <div class="day" style="font-size: 2em; color: #b6b6b6;line-height: 1em;">04</div>
                      <div style="font-size: 0.5em; color: #b6b6b6; ">2020-05</div>
                    </div>
                    <div class="news-title" style="display: inline-block; margin-left: 1em; font-size: 1em;vertical-align:middle; text-align: left;"><a href="#" style="color: #303E4F;">这里是标题啊啊试测试测试驱蚊器二无沃翁啊</a></div>
                  </div>
                  <el-divider style="margin-bottom: -1em;"></el-divider>
                </li>
              </ul>
            </div>
          </el-col>

          <el-col :span="6" :push="2" style="height: 3em">
            <div style="display: inline-block; vertical-align:middle;float: left">
              <ul>
                <li>
                  <div class="in-line" style="display: inline-block; vertical-align:middle; margin-bottom: -1.5em;">
                    <div class="time" style="display: inline-block; vertical-align:middle;align-content: flex-start">
                      <div class="day" style="font-size: 2em; color: #b6b6b6;line-height: 1em;">04</div>
                      <div style="font-size: 0.5em; color: #b6b6b6; ">2020-05</div>
                    </div>
                    <div class="news-title" style="display: inline-block; margin-left: 1em; font-size: 1em;vertical-align:middle;text-align: left;"><a href="#" style="color: #303E4F;">这里是标题啊啊测试沃尔沃若翁</a></div>
                  </div>
                  <el-divider style="margin-bottom: -1em;"></el-divider>
                </li>
              </ul>
            </div>
          </el-col>
        </el-row>
        <!--news end-->

      </el-main>
    </el-container>


    <div class="home-friends">
      <div class="friends-container">
        <h1>合作伙伴</h1>
        <ul>
          <li v-for="item in 5" :key="item">
            <!--img :src="`../../../static/img/friends/clients-logo0${item}.png`" -->
            <img :src="`../../../static/img/friends/clients-logo01.png`" alt="保利物业" style="width: 80px; height: 80px">
          </li>
        </ul>
      </div>
    </div>

  </div>

</template>
<script>

  export default {
    name: "Home",
    bannerh: '500px',
    data() {
      return {
        slider_index: 0,
        sliderList: [
          {
            title: '实力，让情怀落地',
            abstract: '黑格服装，您的服装管家',
            img: 'slider01.jpg',
            link: ''
          },
          {
            title: '不喧哗，自有声',
            abstract: '黑格服装',
            img: 'slider02.jpg',
            link: ''
          },
          {
            title: '赢不是全部，想要赢才是。',
            abstract: '黑格服装',
            img: 'slider03.jpg',
            link: ''
          }
        ],
        kind: [
          {
            title: '私人定制',
            info: '量体裁衣，彰显您的个人魅力'
          },
          {
            title: '高端品质',
            info: '优选面料，汇聚行业先进裁剪工艺'
          },
          {
            title: '一站式服务',
            info: '10天内送货上门'
          },
          {
            title: '365天无忧售后',
            info: '尊享优质定制体验'
          }
        ],
        services: [
          {
            title: '男士西装',
            info: '时尚男装，休闲西服，商务正装，满足您的多样需求'
          },
          {
            title: '女士西装',
            info: '修身剪裁，简约设计，彰显您的高雅气质'
          },
          {
            title: '工装',
            info: '支持保洁，厨师服，工程服，物业安保服，文化衫等'
          }
        ]
      }
    },
    created() {
      this.$emit('headFix', ['fixed', false]);
    },
    methods: {
      loadAnimate(index) {
        this.slider_index = index;
      },
    },
    //设置banner高度自适应
    beforeMount() {
      setHeightbyWindow(this);
    },
    mounted() {
      // 通过捕获系统的onresize事件触发重新设置banner高度
      window.onresize =function seth(){
      setHeightbyWindow(this);
      }
    }
  }

  function setHeightbyWindow(that){
    let w = window.innerWidth;
    let h;
    if (w > 1180) {
      h = 500
    } else {
      h = 0.31 * w
    }
    that.bannerh = h + 'px';
    console.log(that.bannerh)
  }
</script>
<style lang="scss" scoped>
  @mixin self_icon {
    &::before {
      border-left: 50px solid #DADADA;
      border-right: 50px solid #DADADA;
      bottom: 0;
      content: "";
      height: 1px;
      margin-left: -70px;
      position: absolute;
    }
    &::after {
      background: #f0f0f0 none repeat scroll 0 0 padding-box content-box;
      border-bottom: 1px solid #DADADA;
      border-left: 1px solid #DADADA;
      bottom: -10px;
      content: "";
      left: 50%;
      margin-left: -16px;
      padding: 0 0 8px 8px;
      position: absolute;
      transform: rotate(-45deg);
    }
  }

  figure {
    color: #ffffff;
    text-align: left;

    &::before {
      background: rgba(0, 0, 0, 0.4) none repeat scroll 0 0;
      content: "";
      height: 100%;
      position: absolute;
      width: 100%;
    }

    figcaption {
      bottom: 0;
      left: 3%;
      margin: 0 auto;
      position: absolute;
      right: 6%;
      top: 40%;
      width: 100%;
      padding: 0 10%;

      h1 {
        font-size: 1vm;
      }

      p {
        font-size: 1vm;
      }

      .slider-button {
        background-color: #3F3F3F;
        border-color: #3F3F3F;
        color: #ffffff;
        width: 1vm;
        height: 1vm;
        font-size: 1vw;
        transition: transform 2s;

        &:hover {
          transform: translateY(10px);
        }
      }
    }
  }

  .home-kind {
    box-sizing: border-box;
    background-color: #EBEEF5;
    padding: 0 5%;
    display: flex;

    li {
      padding: 1%;
      text-align: left;
      position: relative;
      box-sizing: border-box;
      width: 25%;

      h3 {
        display: inline-block;

        div {
          margin-top: 1%;
          height: 2px;
          width: 40px;
          background-color: #0984E3;
        }
      }

      p {
        margin-top: 1.5%;
        font-size: 14px;
        color: gray;
      }

      h3 > div {
        transition: width .5s;
      }

      &:hover {
        background-color: #ffffff;
        transition: background-color .5s;
        h3 > div {
          width: 100%;
        }
      }

      &:not(:first-child)::before {
        content: '';
        position: absolute;
        width: 1px;
        height: 80%;
        left: 0;
        background-color: #D6D6D6;
      }

    }
  }

  .home-service {
    margin-top: 3%;

    h1 {
      position: relative;
      @include self_icon;

      &::before {
        left: 49.8%;
        top: 174%;
        width: 40px;
      }

      &::after {
        height: 20px;
        left: 50%;
        top: 140%;
        width: 19px;
      }
    }

    & > p {
      margin-top: 5%;
      color: gray;
    }

    ul {
      margin-top: 5%;
      padding: 0 10%;
      display: grid;
      grid-template-columns: repeat(3, 33.33333%);

      li {
        .product-box {
          margin-left: 15%;
          display: inline-block;
          width: 10vm;
          height: 25vm;
          border-radius: 5%;
          box-shadow: 5px 5px 2px #888888;
          overflow: hidden;

          img:hover {
            transform: scale(1.1);
          }
          img {
            width: 100%;
            height: 30%;
            transition:1s;
            overflow: hidden;
          }
          .product-info {
            margin-top: 5%;
            .product-title{
              color: #8c939d;
            }
            .product-content{
              color: #3F3F3F;
              font-size: 1em;
            }
          }
        }
      }

    }
  }

  .home-friends {
    margin-top: 2%;
    height: 35vh;
    padding: 20px 0;
    background: url(../../../static/img/head-view/clients-bg.jpg);
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    position: relative;

    &::before {
      position: absolute;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.4);
      content: "";
      left: 0;
      top: 0;
    }

    .friends-container {
      padding-right: 8%;
      padding-left: 8%;
      position: relative;

      h1 {
        font-size: 45px;
        color: #ffffff;
        @include self_icon;

        &::before {
          left: 50%;
          top: 144%;
          width: 29.5px;
        }

        &::after {
          height: 12px;
          left: 50%;
          top: 130.5%;
          width: 12px;
        }
      }

      ul {
        display: flex;
        margin-top: 2%;
        position: absolute;
        margin-left: 42%;
        margin-right: 42%;
        transform: translateX(-50%);
      }
    }
  }

  // 动画类
  .bounceInDown {
    animation: bounceInDown 1s linear;
  }

  .fadeInUp {
    animation: fadeInUp 1s linear;
  }
</style>
