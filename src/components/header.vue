<script setup>
import { ref,watch,onMounted,computed,onUnmounted,getCurrentInstance} from 'vue'

const isTop = ref(false)

onMounted(() => {
    window.addEventListener('scroll', doScroll)
})
onUnmounted(() => {
    window.removeEventListener('scroll', doScroll)
})
function openWindow(e) {
    window.open(e)
}
const doScroll = (event) => {
   // 滚动条距文档顶部的距离
   let scrollTop =window.pageYOffset ||document.documentElement.scrollTop ||document.body.scrollTop;
  
  console.log(scrollTop)
  if(scrollTop>60){
    isTop.value = true
  }else{
    isTop.value = false
  }
}
</script>

<template>
    <div class="header-content">
        <div class="header" :style="isTop?'position: fixed;':''">
            <div class="logo">
                <img src="../assets/img/logo.png" alt="">
            </div>
            <div class="center">
                <span class="item" @click="openWindow('https://app.smartmall.ai/pages/project/project')">Project</span>
                <span class="ido"></span>
                <span class="item" @click="openWindow('https://app.smartmall.ai/pages/market/market')">Market</span>
                <span class="ido"></span>
                <span class="item" @click="openWindow('https://app.smartmall.ai/pages/news/news')">media</span>
            </div>
            <div class="right-btn-box">
                <div class="btn" @click="openWindow('https://app.smartmall.ai')">Launch App</div>
            </div>
        </div>
    </div>
</template>



<style lang="less">
.header-content{
    height: 66px;
    background-color: var(--color-background);
    color: var(--color-text);
    
    .header{
        background-color: var(--color-background);
        left: 0;
        top: 0;
        height: 66px;width: 100%;
        padding: 0 48px;
        box-sizing: border-box;
        display: flex;
        align-items: center;
        justify-content: space-between;
        z-index: 9;
        >.logo{
            >img{
                width: 205px;
                height: 30px;
            }
        }
        .center{
            border: 0.5px solid rgba(229, 231, 235, 0.50);
            border-radius: 21px;
            color: var(--color-text2);
            font-size: 16px;
            padding: 11.5px 20px;
            display: flex;
            align-items: center;
            height: 43px;
            box-sizing: border-box;
            .ido{
                width: 4px;
                height: 4px;
                background: #E5E7EB;
                border-radius: 50%;
                margin: 0 10px;
            }
            .item{
                cursor: pointer;
                transition: 0.25s;
            }
            .item:hover{
                color: #FF01F4;
            }
        }
        .right-btn-box{
            .btn{
                cursor: pointer;
                height: 42px;
                width: 140px;
                text-align: center;
                line-height: 42px;
                border-radius: 4px;
                background: var(--color-btn-gradient);
                transition: 0.35s;
            }
            .btn:hover{
                background: var(--color-btn-reverse);
                transform:scale(1.05);
            }
           
        }
    }
}
@media screen and (max-width: 1000px) {
    .header-content{
        .header{
            padding: 0 17px;
            >.logo{
                >img{
                    width: 122px;
                    height: 18px;
                }
            }
            .center{
                display: none;
            }
        }
    }
}
</style>