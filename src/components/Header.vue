<template>
  <div v-bind:class="{pcStyle : listShow , mobileStyle : listShow === false}">
    <header :style="{backgroundColor: bg_color, position: hd_position}">
      <div>
        <div :class="{img_hover: hover_flag}" class="web_icon">
          <img src="../../static/img/brand-heige.png" alt="定制西装" @click="toHome" style="width: 0.5vm; height: 1vm">
        </div>
        <ul>
          <li v-for="(item,index) in titleList" :key="index" @click="selected(item.title)"
              :class="{ active: active == item.title }" role="presentation">
            <router-link :to="item.link" :class="{active: active == item.title}">{{ item.title }}</router-link>
          </li>
        </ul>
        <span v-if="listShow === false" class="el-icon-menu"></span>
        <!--如果屏幕宽度小于 768，则展示一个菜单图标，鼠标悬浮再条形展示菜单-->

      </div>
    </header>
  </div>
</template>

<script>
  export default {
    name: "Header",
    props: {
      bg_color: {
        type: String,
        default: 'transparent'
      },
      hd_position: {
        type: String,
        default: 'fixed'
      },
      hover_flag: {
        type: Boolean,
        default: true
      }
    },
    data() {
      return {
        listShow: true,
        active: '首页',
        titleList: [
          {
            title: '首页',
            link: '/home'
          },
          {
            title: '团体定制',
            link: '/product'
          },
          {
            title: '私享定制',
            link: '#'
          },
          {
            title: '合作案例',
            link: '#'
          },
          {
            title: '新闻资讯',
            link: '#'
          },
          {
            title: '关于我们',
            link: '#'
          }/*,
                {
                    title: '500',
                    link: '/error-500'
                }*/
        ]

      }
    },
    beforeUpdate() {
      this.Switching();
    },
    mounted() {
      this.active = this.$route.meta.nav;
      window.addEventListener('resize', this.Switching);
      this.Switching();
    },
    methods: {
      selected(title) {
        this.active = title;
      },
      toHome() {
        this.$router.push('/home');
        this.active = '首页';
      },
      Switching() {
        let that = this
        let w = document.documentElement.clientWidth || document.body.clientWidth
        if (w >= 769) {
          that.listShow = true; //显示pc菜单
        }
        if (w < 769) {
          that.listShow = false;  //显示mobile菜单
        }
        /*if(w<450){
          that.searchInput=false  //隐藏input框
          that.logopPic=true  //显示logo
          that.sideList=false //隐藏侧边栏
        }else{
          that.sideList=true  //显示侧边栏
        }
        if(w>1000){
          that.searchInput=true  //显示input框
        }else{
          that.searchInput=false  //隐藏input框
        }*/
      }

    }
  };
</script>

<style lang="scss" scoped>
  $white: #ffffff;
  @mixin rim {
    background: transparent none repeat scroll 0 0;
    content: "";
    height: 10px;
    position: absolute;
    width: 25px;
    visibility: hidden;
    transition: .3s ease;
    opacity: 0;
  }

  .pcStyle {
    header {
      color: $white;
      position: fixed;
      top: 0;
      left: 0;
      z-index: 999;
      width: 100%;
      padding: 2% 0;
      transition: background-color 1.5s;

      & > div {
        display: flex;
        justify-content: space-between;
        margin: 0 10%;

        .img_hover:hover {
          &::before {
            content: "";
            height: 555px;
            width: 100%;
            position: absolute;
            left: 0%;
            top: 0;
            background-color: transparent;
            background-image: -webkit-linear-gradient(-30deg, transparent 30%, #fff 50%, transparent 70%);
            /* 设置渐变的背景，按对角线渐变 */
            background-blend-mode: hard-light;
            /*设置背景为混合模式下的强光模式*/
            background-size: 200%;
            animation: shine 5s forwards;
            /*给背景添加动画改变位置*/
          }
        }

        .web_icon {
          img {
            position: absolute;
            z-index: inherit;
            cursor: pointer;
          }
        }

        ul {
          font-family: "Arial", "Microsoft YaHei", "黑体", "宋体", sans-serif;
          font-size: 1em;
          font-weight: bold;
          display: flex;
          list-style: none;

          li {
            margin-right: 5px;
            box-sizing: border-box;
            position: relative;

            a {
              display: block;
              line-height: 1vm;
              padding: 6px 15px;
              text-decoration: none;
              box-sizing: border-box;
              color: $white;
              position: relative;
              background-color: transparent;
              text-transform: uppercase;
              transition: .3s ease;

              &.active {
                color: #f0f0f0;

                &::before {
                  visibility: visible;
                  opacity: 1;
                  left: 0;
                }

                &::after {
                  visibility: visible;
                  opacity: 1;
                  right: 0;
                }
              }

              &:hover {
                background: none;
                color: #f0f0f0;
                outline: none;

                &::before {
                  visibility: visible;
                  opacity: 100;
                  left: 0;
                }

                &::after {
                  visibility: visible;
                  opacity: 100;
                  right: 0;
                }
              }

              &::before {
                @include rim;
                border-left: 1px solid #f0f0f0;
                border-top: 1px solid #f0f0f0;
                top: 0;
                left: -70px;
              }

              &::after {
                @include rim;
                border-right: 1px solid #f0f0f0;
                border-bottom: 1px solid #f0f0f0;
                bottom: 0;
                right: 70px;
              }
            }
          }
        }
      }
    }
    }

    .mobileStyle {
      header {
        img{
          width: 20px;
          height: 10px;
          position: absolute;
          z-index: inherit;
          cursor: pointer;
        }
        ul{
          //display: none;
          float: left;
          width: 100%;

        }
        span{
          color: white;

        }
      }
    }

    // 动画
    @keyframes shine {
      from {
        background-position: 130%;
      }
      to {
        background-position: -50%;
      }
    }
</style>
