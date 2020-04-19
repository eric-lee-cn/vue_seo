<template>
    <div class="product-detail">
        <figure>
            <figcaption>
                <h1>男士西装</h1><br>
                <p></p>
            </figcaption>
            <img :src="`../../../static/img/product/work0${$route.params.id}.jpg`" width="100%" height="500px">
        </figure>
        <div class="detail-content">
            <div class="detail-block">
                <div class="elem-quote"><h2>产品概述</h2></div>
                <div class="product-info">
                  湖南黑格服装有限公司主要从事企业商务工装定做，行政制服定做，员工工装定做。产品包括男女式西服、西裤、马甲、裙子、衬衫、风衣、文化衫等。公司主要产品定位于“时尚职业装”，能够兼顾穿着之人的职业所需、舒适程度和潮流追求。
                </div>
            </div>
            <div class="detail-block">
                <div class="elem-quote"><h2>关于我们</h2></div>
                <ul>
                  <li>公司主要产品定位于“时尚职业装”，能够兼顾穿着之人的职业所需、舒适程度和潮流追求，并遵循大规模量身定制的服务特色，满足不同行业不同岗位的全方位需求。</li>
                  <li>公司引进美国CAD电脑服装设计系统设计，德国杜克普专业西装缝制设备生产和电脑立体整烫设备整烫，构建了国际定制西服专业生产线。工艺上采用欧洲经典样版和名牌辅料，经过128道工序、200多道子工序及10多年丰富经验，精工细作，制作出的每件西服合体流畅，尽显您的品位和修养。</li>
                  <li>多年来客户来自物业、地产、建筑、销售、物流、医疗、美容、酒店等行业。包括<strong>佳兆业地产</strong>、<strong>中海梅溪湖地产有限公司</strong>、<strong>保利物业管理有限公司</strong>、<strong>星润物业</strong>、<strong>方正证券</strong>、湖南嘉华地产有限公司、至美物业管理有限公司、湖南高新置业有限公司、湖南汇景物业管理有限公司、万科里梅溪郡、湘茶集团、好小子机器人、神龙大酒店、伯明汉教育集团、明城国际大酒店、长沙美莱医疗整形医院、湖南雅美集团、长沙爱思特医疗美容院、湖南宏雅湘美健康管理有限公司等。</li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'product-detail',
    data(){
        return {

        }
    },
    mounted(){
        window.scroll(0,0);
        this.$emit('headFix', ['fixed',false]);
    },
    methods:{

    }

}
</script>
<style lang="scss" scoped>
    .product-detail {
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
        .detail-content {
            padding: 2% 5%;
            .detail-block {
                margin-bottom: 5%;
                .elem-quote {
                    text-align: left;
                    text-indent: 1em;
                    margin-bottom: 10px;
                    line-height: 22px;
                    border-left: 5px solid #009688;
                    border-radius: 0 2px 2px 0;
                }
                .product-info {
                    text-align: left;
                    font-size: 15px;
                    line-height: 25px;
                }
                ul {
                    text-align: left;
                    padding-left: 2%;
                    list-style-type: disc;
                }
            }
        }

    }

</style>
