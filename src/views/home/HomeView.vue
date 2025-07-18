<script setup>
// import TheWelcome from '../../components/TheWelcome.vue' 
import Footer from '../../components/footer/footer.vue' 
import { ref,watch,onMounted,computed,onUnmounted,getCurrentInstance} from 'vue'

const topImgList = ref([
    {name:'matic',type:"Polygon"},
    {name:'solana',type:"Solana"},
    {name:'bnb',type:"BNB Chain"},
    {name:'eth',type:"Ethereum"},
    {name:'arb',type:"Arbitrum"},
    {name:'op',type:"Optimism"},
    // {name:require('../../assets/img/home/chain/matic.png'),type:"Polygon"},
    // {name:require('../../assets/img/home/chain/solana.png'),type:"Solana"},
    // {name:require('../../assets/img/home/chain/bnb.png'),type:"BNB Chain"},
    // {name:require('../../assets/img/home/chain/eth.png'),type:"Ethereum"},
    // {name:require('../../assets/img/home/chain/arb.png'),type:"Arbitrum"},
    // {name:require('../../assets/img/home/chain/op.png'),type:"Optimism"},
])
const timer = ref(null)

onMounted(() => {
  
  timer.value = setInterval(function(){
    swiperFun()
  },3000)
})
onUnmounted(() => {
  
  clearInterval(timer.value)
  timer.value = null
})

function swiperFun(){
  topImgList.value.push(topImgList.value[0])
  topImgList.value.shift()//删除数组第一个元素
  
}
function getImageUrl(name) {
    return new URL(`/src/assets/img/home/chain/${name}.png`, import.meta.url).href;
}
function openWindow(e) {
  window.open(e)
}
</script>

<template>
  <!-- <main>
    <TheWelcome />
  </main> -->
  <div id="home">
    <div class="content">
      <div class="top-box">
        <div class="top">
          <div class="title">
            <img class="brackets" src="../../assets/img/home/top-left.png" alt="">
            
            <div class="swiper-box">
              <div class="item" v-for="(item,index) in topImgList" :key="index">
                <!-- <img class="polygon" src="../../assets/img/home/matic.png" alt="">
                <span>Polygon</span> -->
                <img class="polygon" :src="getImageUrl(item.name)" alt="">
                <span>{{ item.type }}</span>
              </div>
             
            </div>
            <img class="brackets" src="../../assets/img/home/top-right.png" alt="">
            <span>Ecosystem</span>
          </div>
          <div class="title">
            <span>Aggregator</span>
            <img class="logo-text" src="../../assets/img/home/top-logo.png" alt="">
            <span>Smartmall</span>
          </div>
          <div class="desc">Build an infinitely scalable multi-chain network ecosystem Aggregator.</div>
        </div>
        <div class="logo-collection">
          <img class="img" src="../../assets/img/home/logo-collection.png" alt="">
          <div class="img-mobile">
            <img src="../../assets/img/home/logo-collection-m.png" alt="">
          </div>
          <p class="title">
            The most thriving ecosystem
          </p>
          <p class="desc">
            Builders, traders and contributors participate together in our ecosystem aggregator that is open and accessible to everyone
          </p>
          <div class="btn" @click="openWindow('https://app.smartmall.ai')">
            Launch App
          </div>
        </div>
      </div>

      <div class="web3-box">
        <div class="title">
          <img src="../../assets/img/home/web3/title.png" alt="">
          <p>
            <span>Our </span>
            <span class="color">Mission</span>
            <span> of web3</span>
          </p>
        </div>
        <div class="item-box">
          <div class="item">
            <img class="icon" src="../../assets/img/home/web3/icon1.png" alt="">
            <img class="tips-img" src="../../assets/img/home/web3/item-1.png" alt="">
            <p class="desc">
              Anyone can enjoy the immersive experience through the 'smart mall', have an exclusive identity as a 'meta-resident', publish collections, and cast their own digital assets.
            </p>
            <p class="b-title">Advantage</p>
          </div>
          <div class="item item2">
            <img class="icon" src="../../assets/img/home/web3/icon2.png" alt="">
            <img class="tips-img"  src="../../assets/img/home/web3/item-2.png" alt="">
            <p class="desc">
              NFT owners will receive corresponding rights and interests, and can enhance decentralized network value interaction while freely enjoying the ecological fun on the chain.
            </p>
            <p class="b-title">Rights and interests</p>
          </div>
          <div class="item item3">
            <img class="icon" src="../../assets/img/home/web3/icon3.png" alt="">
            <img class="tips-img" src="../../assets/img/home/web3/item-3.png" alt="">
            <p class="desc">
              A decentralized business network, is committed to building the NFT aggregation digital platform with the highest brand awareness, and becoming a bridge between traditional industries and Web3
            </p>
            <p class="b-title">Vision</p>
          </div>
        </div>
        <div class="line">
          <span></span>
          <img src="../../assets/img/home/web3/star.png" alt="">
          <span></span>
        </div>
        <div class="title-introduce">
          <p class="title">Engaging in eco-construction</p>
          <p class="desc">Start with our ecosystem construction</p>
        </div>
        <div class="introduce">
          <div class="item">
            <div class="up">
              <img src="../../assets/img/home/web3/b1.png" alt="">
              <span>Start with $GUP</span>
            </div>
            <p class="desc">
              GUP is a utility token used within the SmartMall ecosystem, serving critical functions. Not only is GUP used to reward user participation and interaction, but it also acts as the sole token for minting SMT (SmartMall Token), thus holding a significant position within the platform.
            </p>
          </div>
          <div class="item">
            <div class="up">
              <img src="../../assets/img/home/web3/b2.png" alt="">
              <span>Invest in $SMT</span>
            </div>
            <p class="desc">
              SMT is the native token of the SmartMall platform, serving as the primary currency for transactions and operations both within and outside the platform. SMT is used for various transactions on the platform, such as purchasing NFTs and paying for services. It is exclusively minted using GUP, fully open-source, and decentralized.
            </p>
          </div>
          <div class="item">
            <div class="up">
              <img src="../../assets/img/home/web3/b3.png" alt="">
              <span>Get free $USMT</span>
            </div>
            <p class="desc">
              USMT (USMT Token) is a weight token with a total supply of 10 billion. Users can earn USMT by daily check-ins and adding liquidity to liquidity pools (LP). USMT is primarily used for sharing mainstream cryptocurrencies, participating in SMT transactions, and serving as a payment token for various applications within the platform.
            </p>
          </div>
          <div class="item">
            <div class="up">
              <img src="../../assets/img/home/web3/b4.png" alt="">
              <span>Build in Smartmall</span>
            </div>
            <p class="desc">
              We build SMARTMALL together through community governance and incentive mechanisms. Participants can propose and vote on the platform's development direction and earn token rewards for their contributions and interactions. Developers can integrate innovative applications through open APIs and tools, while users can promote and utilize the platform, collectively advancing the SMARTMALL ecosystem.
            </p>
          </div>
        </div>
      </div>

      <div class="build-box">
        <div class="title">Building with Smartmall ,powerful ecosystems</div>
        <div class="icon-box">
          <img src="../../assets/img/home/build/1.png" alt="">
          <img src="../../assets/img/home/build/2.png" alt="">
          <img src="../../assets/img/home/build/3.png" alt="">
          <img src="../../assets/img/home/build/4.png" alt="">
          <img src="../../assets/img/home/build/5.png" alt="">
          <img src="../../assets/img/home/build/6.png" alt="">
          <img src="../../assets/img/home/build/7.png" alt="">
          <img src="../../assets/img/home/build/8.png" alt="">
          <img src="../../assets/img/home/build/9.png" alt="">
          <img src="../../assets/img/home/build/10.png" alt="">
          <img src="../../assets/img/home/build/11.png" alt="">
          <img src="../../assets/img/home/build/12.png" alt="">
          <img src="../../assets/img/home/build/13.png" alt="">
          <img src="../../assets/img/home/build/14.png" alt="">
          <img src="../../assets/img/home/build/15.png" alt="">
          <img src="../../assets/img/home/build/16.png" alt="">
          <div class="flex-row">
            <img @click="openWindow('https://x.com/metaspacedao')" src="../../assets/img/home/build/17.png" alt="">
            <img @click="openWindow('https://x.com/C_ChainOfficial')" src="../../assets/img/home/build/18.png" alt="">
          </div>
          
          <div class="flex-row">
            <img @click="openWindow('https://t.me/polysphere_cn')" src="../../assets/img/home/build/19.png" alt="">
          </div>
          
        </div>
        <div class="build-protcol">
          <p class="title">
            <span>Build the next with </span>
            <span class="color">SMT protocol</span>
          </p>
          <div class="protcol-box">
            <div class="item" @click="openWindow('https://smartmall.gitbook.io/guide/protocol/erc-7527-smt')">
              <div class="title-box">
                <img src="../../assets/img/home/build/icon-1.png" alt="">
                <div class="tight-c">
                  <div>
                    <span>Multi-chain</span>
                  </div>
                </div>
              </div>
              <div class="img-right">
                <img src="../../assets/img/home/build/i1.png" alt="">
              </div>
              <p class="title">
                ERC-7527-SMT
              </p>
              <p class="desc">
                ERC-7527, also known as the Token Bound FunctionOracle Automated Market Maker (FOAMM), is a protocol designed to enhance the NFT ecosystemthrough a trustless framework. It aims to address the challenges
              </p>
            </div>
            <div class="item" @click="openWindow('https://smartmall.gitbook.io/guide/protocol/smt-80-20-revenue-sharing-protocol-specification')">
              <div class="title-box">
                <img src="../../assets/img/home/build/icon-2.png" alt="">
                <div class="tight-c">
                  <div>
                    <span>Powered by </span>
                    <img src="../../assets/img/home/build/t2.png" alt="">
                    <span>SMT</span>
                  </div>
                  <img src="../../assets/img/home/build/link-arrow.png" alt="">
                </div>
              </div>
              <div class="img-right">
                <img src="../../assets/img/home/build/i2.png" alt="">
              </div>
              <p class="title">
                80/20 Revenue sharing Protocol
              </p>
              <p class="desc">
                The SMT 80/20 Revenue Sharing Protocole establishes a standardized method for automatic revenue distribution within the SmartMall Token ecosystem, utilizing a fixed 80/20 split mechanism.
              </p>
            </div>
            <div class="item" @click="openWindow('https://smartmall.gitbook.io/guide/protocol/smt-dynamic-minting-protocol-specification')">
              <div class="title-box">
                <img src="../../assets/img/home/build/icon-3.png" alt="">
                <div class="tight-c">
                  <div>
                    <span>Powered by </span>
                    <img src="../../assets/img/home/build/t3.png" alt="">
                    <span>Mars</span>
                  </div>
                  <img src="../../assets/img/home/build/link-arrow.png" alt="">
                </div>
              </div>
              <div class="img-right">
                <img src="../../assets/img/home/build/i3.png" alt="">
              </div>
              <p class="title">
                Dynamic Minting Protocol
              </p>
              <p class="desc">
                The SMT Dynamic Minting Protocol establishes a scalable and adaptive mechanism for the minting of SmartMall Tokens (SMT) based on market conditions and token supply dynamics
              </p>
            </div>
          </div>
          <div class="protcol-box protcol-box-bottom">
            <div class="item" @click="openWindow('https://smartmall.gitbook.io/guide/middleware-solutions')">
              <div class="title-box">
                <img src="../../assets/img/home/build/icon-4.png" alt="">
                <div class="tight-c">
                  <div>
                    <span>Powered by </span>
                    <img src="../../assets/img/home/build/t4.png" alt="">
                  </div>
                  <img src="../../assets/img/home/build/link-arrow.png" alt="">
                </div>
              </div>
              <div class="img-right">
                <img src="../../assets/img/home/build/i4.png" alt="">
              </div>
              <p class="title">
                Middleware Solutions
              </p>
              <p class="desc">
                We build the APl Gateway and Cross-Chain Protocol Bridge.
              </p>
            </div>
            <div class="item" @click="openWindow('https://app.smartmall.ai')">
              <div class="title-box">
                <img src="../../assets/img/home/build/icon-5.png" alt="">
                <div class="tight-c">
                  <div>
                    <span>Powered by </span>
                    <img src="../../assets/img/home/build/t2.png" alt="">
                    <span>SMT</span>
                  </div>
                  <img src="../../assets/img/home/build/link-arrow.png" alt="">
                </div>
              </div>
              <div class="img-right">
                <img src="../../assets/img/home/build/i5.png" alt="">
              </div>
              <p class="title">
                More Possibilities
              </p>
              <p class="desc">
                Explore a growing ecosystem of apps with Smartmall.
              </p>
            </div>
            
          </div>
        </div>
      </div>

      <div class="community-box">
        <div class="community-banner">
          <div class="left">
            <p class="title">
              <span>Governed by the Fully-</span>
              <span class="color">Decentralized Community</span>
            </p>
            <p class="desc">A fully decentralized community governed protocol with 108 DAOs and 69,389 Token holders.</p>
            <!-- <div class="btn">
              <span>Vote now</span>
              <img src="../../assets/img/home/community/arrow-up-right.png" alt="">
            </div> -->
          </div>
        </div>
        <div class="security-box">
          <div class="title">
            Smartmall empowers security to innovate,
          </div>
          <div class="security-item">
            <div class="item">
              <img class="img-1" src="../../assets/img/home/community/1.png" alt="">
              <div class="text-box">
                <p class="title">Audits & Safety Module</p>
                <p class="desc">Audited by top-tier security firms , Security is our top priority. And Smart protocol is secured with a safe backstop for protocol insolvency</p>
              </div>
              <img class="img-2" src="../../assets/img/home/community/1.png" alt="">
            </div>
            <div class="item">
              <img class="img-1" src="../../assets/img/home/community/2.png" alt="">
              <div class="text-box">
                <p class="title">Bug Bounty</p>
                <p class="desc">We want the Smartmall protocol to be the best it can be, so we're calling on our community to help us find any bugs or vulnerabilities. Submit a bug here through our community driven bug bounty program on Immunefi.</p>
              </div>
              <img class="img-2" src="../../assets/img/home/community/2.png" alt="">
            </div>
          </div>
        </div>
      </div>

      <div class="connect-box">
        <p class="title">
          Connect with Smartmall.
        </p>
        <div class="connect-item">
          <div class="item" @click="openWindow('https://smartmall.gitbook.io/guide/smartmall-platform-overview')">
            <div class="up">
              <img class="icon" src="../../assets/img/home/connect/icon-1.png" alt="">
              <img class="right-icon" src="../../assets/img/home/connect/top-right.png" alt="">
            </div>

            <div class="msg-box">
              <div class="text">
                <p class="title">Middleware Solutions</p>
                <p class="desc">We build the APl Gateway and Cross-Chain Protocol Bridge.</p>
              </div>
              <img src="../../assets/img/home/connect/1.png" alt="">
            </div>

          </div>
          <div class="item" @click="openWindow('https://smartmall.gitbook.io/guide/contact-us')">
            <div class="up">
              <img class="icon" src="../../assets/img/home/connect/icon-2.png" alt="">
              <img class="right-icon" src="../../assets/img/home/connect/top-right.png" alt="">
            </div>

            <div class="msg-box">
              <div class="text">
                <p class="title">More Possibilities</p>
                <p class="desc">Explore a growing ecosystem of apps with Smartmall.</p>
              </div>
              <img src="../../assets/img/home/connect/2.png" alt="">
            </div>

          </div>
        </div>
        <div class="connect-item connect-item2">
          <div class="item" @click="openWindow('https://x.com/SmartMall_ai')">
            <div class="up">
              <img class="icon" src="../../assets/img/home/connect/icon-3.png" alt="">
              
              <div class="right-c" >
                <p>@smartmall_ai</p>
                <img class="right-icon" src="../../assets/img/home/connect/top-right.png" alt="">
              </div>
            </div>

            <div class="msg-box">
              X(Twitter)
            </div>

          </div>
          <div class="item" @click="openWindow('https://t.me/smartmallAI')">
            <div class="up">
              <img class="icon" src="../../assets/img/home/connect/icon-4.png" alt="">
              
              <div class="right-c" >
                <p>@smartmall_ai</p>
                <img class="right-icon" src="../../assets/img/home/connect/top-right.png" alt="">
              </div>
            </div>

            <div class="msg-box">
              Telegram
            </div>

          </div>
          <div class="item" >
            <div class="up">
              <img class="icon" src="../../assets/img/home/connect/icon-5.png" alt="">
              
              <div class="right-c" >
                <p>@smartmall_ai</p>
                <img class="right-icon" src="../../assets/img/home/connect/top-right.png" alt="">
              </div>
            </div>

            <div class="msg-box">
              Discord
            </div>

          </div>
        </div>
      </div>
    </div>
    <Footer></Footer>
  </div>
</template>

<style lang="less" scoped>
@import './home.less';
</style>
