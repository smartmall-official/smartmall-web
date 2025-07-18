<template>
    <div class="footer">
        <div class="footer-container">
            <div class="footer-star">
                <span></span>
                <img src="../../assets/img/footer/star.png" alt="">
                <span></span>
            </div>
            <div class="footer-content">
                <div class="left">
                    <img src="../../assets/img/logo.png" alt="">
                    <div class="link-box">
                        <a href="https://x.com/SmartMall_ai" target="_blank" rel="noopener noreferrer">
                            <img src="../../assets/img/footer/1.png" alt="">
                        </a>
                        <a href="javascript:void(0);" >
                            <img src="../../assets/img/footer/2.png" alt="">
                        </a>
                        <a href="https://smartmall.gitbook.io/guide" target="_blank" rel="noopener noreferrer">
                            <img src="../../assets/img/footer/3.png" alt="">
                        </a>
                        <a href="https://t.me/smartmallAI" target="_blank" rel="noopener noreferrer">
                            <img src="../../assets/img/footer/4.png" alt="">
                        </a>
                    </div>
                </div>
                <div class="right">
                    <span class="copyright">©Smartmall 2024</span>
                </div>
            </div>
        </div>
        
    </div>
</template>

<style lang="less">
.footer{
    .footer-container{
        width: 100%;
        max-width: 1440px;
        margin: 0 auto;
        .footer-star{
            display: flex;
            align-items: center;
            justify-content: space-between;
            >span{
                height: 1px;
                background: #2C2261;
                width: calc(50% - 30px);
            }
            >img{
                width:20px;
                height: 20px;
                margin: 0 20px;
            }
        }
        .footer-content{
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 50px 0;
            .left{
                display: flex;
                align-items: center;
                >img{
                    width: 200px;
                    height: auto;
                    margin-right: 20px;
                }
                .link-box{
                    display: flex;
                    align-items: center;
                    >a{
                        margin: 0 30px;
                        img{
                            width: 32px;
                            height: 32px;
                        }
                    }
                }
            }
            .right{
                .copyright{
                    font-size: 24px;
                }
            }
        }
    }
}
@media screen and (max-width: 1000px) {
    .footer{
        .footer-container{
            .footer-content{
                padding: 30px 0;
                flex-direction: column;
                .left{
                    width: 100%;
                    padding: 0 15px;
                    
                    justify-content: space-between;
                    margin-bottom: 20px;
                    box-sizing: border-box;
                    >img{
                        width: 120px;
                    }
                    .link-box{
                        >a{
                            margin: 0 10px;
                            img{
                                width: 24px;
                                height: 24px;
                            }
                        }
                    }
                }
                .right{
                    .copyright{
                        font-size: 14px;
                    }
                }
            }
        }
    }
}
</style>