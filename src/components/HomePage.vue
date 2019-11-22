<template>
  <div class="sanyuan-container" @click="playVideo">
    <video
      autoplay
      loop
      muted
      :src="videoSrc"
      style="width: 100%;position: absolute;top: 50%;transform: translateY(-50%);filter: blur(10px)contrast(0.5)"
    ></video>
    <div ref="iframeContainer" class="iframe-modal--container" @click="destroyModal">
      <svg t="1574415347329" class="icon can-hover" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="11128" width="200" height="200"><path d="M695.192661 320.135498c-10.117149-10.117149-26.015526-10.117149-36.132675 0L502.244178 476.951306 345.42837 320.135498c-10.117149-10.117149-26.015526-10.117149-36.132675 0s-10.117149 26.015526 0 36.132674L466.111503 513.08398 310.018349 669.177135c-10.117149 10.117149-10.117149 26.015526 0 35.410021 5.058574 5.058574 11.562456 7.226535 18.066337 7.226535s13.007763-2.16796 18.066337-7.226535l156.815808-156.815808 156.815808 156.815808c5.058574 5.058574 11.562456 7.226535 18.066338 7.226535s13.007763-2.16796 18.066337-7.226535c10.117149-10.117149 10.117149-26.015526 0-35.410021L538.376853 512.361327l156.815808-156.815808c10.117149-9.394495 10.117149-26.015526 0-35.410021z" fill="#e6e6e6" p-id="11129"></path><path d="M908.375441 486.345801c-0.722653-13.730416-13.007763-24.570219-26.738179-23.847565-13.730416 0.722653-24.570219 12.285109-23.847565 26.738179 0 6.503881 0.722653 12.285109 0.722653 18.788991 0 198.729711-161.151729 359.88144-359.88144 359.881439S138.749471 706.755116 138.749471 508.025406c0-198.729711 161.151729-359.88144 359.881439-359.88144 52.753705 0 103.33945 10.839802 151.03458 33.242061 5.058574 2.16796 10.839802 5.058574 15.898377 7.949188 12.285109 6.503881 27.460833 1.445307 33.964715-10.839802 6.503881-12.285109 1.445307-27.460833-10.839803-33.964714-5.781228-2.890614-12.285109-6.503881-18.788991-9.394496-54.199012-25.292872-112.011291-37.577982-171.991531-37.577981-226.190543 0-410.467184 184.276641-410.467184 410.467184s184.276641 410.467184 410.467184 410.467184 410.467184-184.276641 410.467184-410.467184c0.722653-7.226535 0.722653-14.45307 0-21.679605z" fill="#e6e6e6" p-id="11130"></path><path d="M865.738885 389.510233m-27.460833 0a27.460833 27.460833 0 1 0 54.921666 0 27.460833 27.460833 0 1 0-54.921666 0Z" fill="#e6e6e6" p-id="11131"></path><path d="M825.270289 300.623853m-27.460832 0a27.460833 27.460833 0 1 0 54.921665 0 27.460833 27.460833 0 1 0-54.921665 0Z" fill="#e6e6e6" p-id="11132"></path><path d="M759.508821 224.745236m-27.460832 0a27.460833 27.460833 0 1 0 54.921665 0 27.460833 27.460833 0 1 0-54.921665 0Z" fill="#e6e6e6" p-id="11133"></path></svg>

      <iframe :src="currentLink" class="iframe-modal"></iframe>
    </div>

    <section class="sanyuan-contaienr--wrap">
      <video
        ref="homeVideo"
        autoplay
        loop
        class="sanyuan-video"
      >
        <source :src="videoSrc"/>
      </video>
      <div class="sanyuan-bottom-navbar">

        <div v-for="(item,idx) in words" :key="idx" class="sanyuan-bottom-content can-hover">
          <svg class="sanyuan-btn">
            <rect id="shape" x="0" y="0" fill="none"></rect>
          </svg>
          <span>
            <p class="txt-shadow" style="margin: 0 20% 0;">{{ item.content }}</p>
            <p class="txt-shadow" style="margin: 0 0 0 20%;font-size: 1.1vw;">{{ item.subtext }}</p>
          </span>
        </div>
      </div>
    </section>
    <aside class="sanyuan-sidebar">
      <div class="sanyuan-sidebar-head can-hover">
        <svg class="sanyuan-btn">
          <rect id="shape" x="0" y="0" fill="none"></rect>
        </svg>
        <span class="txt-shadow">三园工程简介</span>
      </div>
      <div v-for="(item,i) in sidebarImages" :key="i" class="sanyuan-sidebar-image can-hover" @click="showModal(item.link)">
        <img :src="item.img" :alt="item.content"/>
        <span class="txt-shadow">{{ item.content }}</span>
      </div>
    </aside>
  </div>
</template>

<script>
import wufang from '@/assets/wufang.jpg'
import zhaoqiao from '@/assets/zhaoqiao.jpg'
import shuiku from '@/assets/shuiku.jpg'
import tangwan from '@/assets/tangwan.jpg'
import videoSrc from '@/assets/xczxg1.mp4'

export default {
  name: 'HomePage',
  data: () => ({
    videoSrc: videoSrc,
    words: [
      { content: `美丽家园`, subtext: '——哈哈哈哈哈哈哈' },
      { content: '绿色田园', subtext: '——哈哈哈哈哈哈哈' },
      { content: '幸福乐园', subtext: '——哈哈哈哈哈哈哈' }
    ],
    sidebarImages: [
      { content: '吴房村', link: 'https://720yun.com/t/zzlraaj55rim4gmwfr?pano_id=OlQAxQPLmO8qqYMB', img: wufang },
      { content: '水库村', link: 'https://720yun.com/t/2evknlpls8e?scene_id=28657187', img: shuiku },
      { content: '赵桥村', link: 'https://720yun.com/t/4avkn9fbz17?scene_id=29690392', img: zhaoqiao },
      { content: '塘湾村', link: 'https://720yun.com/t/b1vkiwie5il#scene_id=34834366', img: tangwan }
    ],
    currentLink: undefined
  }),
  methods: {
    playVideo () {
      this.$refs.homeVideo.play()
    },
    showModal (url) {
      setTimeout(() => {
        this.currentLink = url
      }, 0)
      this.$refs.iframeContainer.style.transform = 'scale(1,1)'
    },
    destroyModal () {
      this.currentLink = undefined
      this.$refs.iframeContainer.style.transform = 'scale(0,0)'
    }
  }
}
</script>

<style scoped>
  .iframe-modal--container {
    z-index: 1002;
    position: absolute;
    width: 100%;
    height: 100%;
    transform: scale(0,0);
    transition: transform 0.8s ease;
    background: rgba(0, 0, 0, 0.8);
  }

  .iframe-modal--container svg{
    position: absolute;
    z-index: 100;
    top: 10%;
    right: 8vw;
    width: 2vmax;
    height: 2vmax;
    transition: transform 0.4s ease;
  }

  .iframe-modal {
    width: 90%;
    height: 90%;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    border-radius: 5px;
    margin: auto;
  }

  .txt-shadow {
    text-shadow: 8px 5px 15px #000;
  }

  .sanyuan-btn {
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 102;

  }

  .sanyuan-btn rect {
    height: 100%;
    width: 100%;
    stroke: #ffd369;
    stroke-width: 0.6vw;
    stroke-dasharray: 95%, 305%;
    stroke-dashoffset: 208%;
    transition: all 800ms ease;
    box-shadow: 10px 10px 10px black;
  }

  .sanyuan-btn:hover rect {
    stroke-width: 0.4vw;
    stroke-dasharray: 80, 0;
    stroke-dashoffset: 0;
  }

  .sanyuan-sidebar .sanyuan-btn rect{
    stroke-dashoffset: 206%;
  }

  .sanyuan-container {
    width: 100%;
    height: 100%;
    background: black;
    position: relative;
    margin: 0;
    padding: 0;
    z-index: 100;
    overflow: hidden;
  }

  .sanyuan-container .sanyuan-contaienr--wrap {
    position: relative;
    height: 100%;
    width: 1920px;
    left: 50%;
    transform: translateX(-50%);
    background: transparent;
  }

  .sanyuan-video {
    height: 100%;
    width: 100%;
    position: absolute;
  }

  .sanyuan-bottom-navbar {
    display: flex;
    flex: 1 1 auto;
    flex-direction: row;
    position: absolute;
    justify-content: space-around;
    left: 0;
    right: 0;
    bottom: 0;
    padding-bottom: 0.5vw;
    padding-left: 5%;
    padding-right: 5%;
    height: 8vw;
    background: linear-gradient(to bottom, transparent, black)
  }

  .sanyuan-bottom-content {
    position: relative;
    height: 5vw;
    margin: auto;
    width: 30%;
  }

  .sanyuan-bottom-content span {
    font-family: "Microsoft YaHei UI";
    position: absolute;
    width: 100%;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    justify-content: center;
    flex-direction: column;
    font-size: 1.5vw;
    color: white;

  }

  .sanyuan-sidebar {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    width: 20vw;
    margin: 1vw 2vw;
    z-index: 101;
    display: flex;
    flex-direction: column;
    flex: 1 1 auto;
    align-items: center;
    justify-content: center;
    color: white;
  }

  .sanyuan-sidebar .sanyuan-sidebar-image {
    margin: 0.2vw;
    height: 25%;
    width: 100%;
    border-radius: 0.8vw;
    position: relative;
    box-shadow: 0 10px 30px rgba(0, 0, 0, .6);
    overflow: hidden;
    border: 1px solid #ffd369;
  }

  .sanyuan-sidebar .sanyuan-sidebar-image img {
    position: absolute;
    width: 100%;
    top: 50%;
    z-index: -1;
    transform: translateY(-50%);
    border-radius: inherit;
    filter: blur(4px) contrast(.9);
  }

  .sanyuan-sidebar .sanyuan-sidebar-image span {
    position: absolute;
    width: 100%;
    text-align: center;
    top: 50%;
    transform: translateY(-50%);
    font-size: 1.3vw;
  }

  .sanyuan-sidebar .sanyuan-sidebar-head {
    height: 15vh;
    width: 80%;
    margin: 0 2vh 1vh;
    position: relative;
  }

  .sanyuan-sidebar .sanyuan-sidebar-head span {
    font-size: 2vw;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    line-height: 1;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .can-hover:hover {
    cursor: pointer;
    transform: scale(1.1, 1.1);
    transition: transform 0.4s;
  }
</style>
