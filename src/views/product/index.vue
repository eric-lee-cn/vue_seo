<template>
    <div class="product">
        <figure>
            <figcaption>
                <h1>男士西装</h1><br>
                <p>湖南黑格服装有限公司主要从事企业商务工装定做，行政制服定做，员工工装定做。公司主要产品定位于“时尚职业装”，能够兼顾穿着之人的职业所需、舒适程度和潮流追求。</p>
            </figcaption>
            <img src="../../../static/img/head-view/about-header-bg.jpg" width="100%" height="10%">
        </figure>
        <ul class="category" :class="{fix: fix}">
            <li v-for="(item,index) in category" :key="index">
                <div class="outcircle" @click="selected(item)">
                    {{ item.title }}
                    <div class="incircle" :class="{active: active == item.title}"></div>
                </div>
            </li>
        </ul>
        <ul class="products">
            <transition-group enter-active-class="animated zoomInLeft" leave-active-class="animated zoomOutRight">
                <li v-for="(item,index) in products" :key="index">
                    <router-link :to="'/product/'+item.id">
                        <img :src="'../../../static/img/product/'+ item.img" width="250px" height="250px" />
                    </router-link>
                    <div class="inner-text">
                        <h4>{{ item.title }}</h4>
                    </div>
                </li>
            </transition-group>
        </ul>
    </div>
</template>
<script>
export default {
    name: 'product',
    data(){
        return {
            active: '所有',
            fix: false,
            category: [
                {
                    kind: 0,
                    title: '所有',
                    color: '#3F3F3F'
                },
                {
                    kind: 1,
                    title: '男士西装',
                    color: '#3F3F3F'
                },
                {
                    kind: 2,
                    title: '女士西装',
                    color: '#3F3F3F'
                },
                {
                    kind: 3,
                    title: '工装',
                    color: '#3F3F3F'
                }
            ],
            products: [
                {
                    id: 1,
                    kind: 1,
                    img: 'work01.jpg',
                    title: '商务正装'
                },
                {
                    id: 2,
                    kind: 2,
                    img: 'work01.jpg',
                    title: '商务正装'
                },
                {
                    id: 3,
                    kind: 3,
                    img: 'work01.jpg',
                    title: '商务正装'
                },
                {
                    id: 4,
                    kind: 2,
                    img: 'work01.jpg',
                    title: '商务正装'
                },
                {
                    id: 5,
                    kind: 3,
                    img: 'work01.jpg',
                    title: '商务正装'
                },
                {
                    id: 6,
                    kind: 3,
                    img: 'work01.jpg',
                    title: '商务正装'
                }
            ],
            copy_products: []
        }
    },
    mounted(){
        this.copy_products = JSON.parse(JSON.stringify(this.products));
        this.$emit('headFix', ['absolute',true]);
        window.addEventListener('scroll', this.handleScroll);
    },
    methods:{
        selected(item){
            this.active = item.title;
            if(item.kind == 0){
                this.products = this.copy_products;
            }else {
                this.products = this.copy_products.filter(it=>it.kind===item.kind);
            }
        },
        handleScroll(){
            let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
            if(scrollTop >= 555){
                this.fix = true;
            }else {
                this.fix = false;
            }
        }
    }

}
</script>
<style lang="scss" scoped>
    .product {
        figure {
            figcaption {
                color: #ffffff;
                text-align: left;
                position: absolute;
                left: 6%;
                top: 30%;
                h1 {
                    font-size: 2.5rem;
                }
            }
        }
        .fix {
            position: fixed;
            left: 0;
            top: 0;
            right: 0;
            z-index: 2;
        }
        .category {
            padding: 1% 25% 0;
            display: grid;
            grid-template-columns: repeat(4, 25%);
            margin-top: -6%;
            li {
                z-index: 99;
                position: relative;
                .outcircle {
                    color: white;
                    line-height: 4em;
                    position: relative;
                    cursor: pointer;
                    transition: all .5s;
                    &:hover {
                        background-color: #BD395B;
                    }
                    .incircle {
                        position: absolute;
                        left: 0;
                        top: 0;
                        right: 0;
                        bottom: 0;
                        font-size: 1.5em;
                        margin: auto;
                        border: 0px solid transparent;
                        opacity: 0.2;
                        background-color: black;
                        &.active {
                            color: white;
                            //border: 3px solid rgba(255,255,255,.4);
                            animation: self-zoomIn .5s linear;
                        }
                    }
                }

            }

        }
        .products>span{
            margin: 15vh auto;
            width: 80%;
            display: grid;
            grid-template-columns: repeat(3, 33.33333%);
            row-gap: 3%;
            li {
                position: relative;
                overflow: hidden;
                img {
                    transition: all .5s ease-out;
                }
                &:hover img {
                    opacity: 0.8;
                }
                &:hover .inner-text{
                    visibility: visible;
                    top: 78.5%;
                }
                .inner-text {
                    position: absolute;
                    left: 50%;
                    right: 10%;
                    top: 100%;
                    transform: translateX(-50%);
                    background: transparent;
                    height: 20%;
                    width: 250px;
                    background-color: rgba(0,0,0,.5);
                    color: #ffffff;
                    visibility: hidden;
                    transition: all .5s ease-out;
                    h4 {
                        margin-top: 5%;
                    }
                }
            }
        }
    }
// 动画
@keyframes self-zoomIn {
  from {
    border: 0px solid transparent;
    transform: scale3d(0.3, 0.3, 0.3);
  }

  50% {
    border: 3px solid #ffffff;
  }

  80% {
    border: 3px solid #ffffff;
  }

  100% {
    border: 3px solid rgba(255,255,255,.4);
  }
}
</style>
