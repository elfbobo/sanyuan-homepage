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
    <div ref="modalContainer" class="iframe-modal--container introduction-bg" @click="hideModal">
      <div class="introduction-modal">
        <svg
          class="intro-border1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          width="6.632cm" height="6.667cm">
          <image x="0px" y="0px" width="80%" height="80%"
                 xlink:href="data:img/png;base64,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"/>
        </svg>
        <svg
          class="intro-border2"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          width="6.632cm" height="6.667cm">
          <image x="0px" y="0px" width="80%" height="80%"
                 xlink:href="data:img/png;base64,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"/>
        </svg>
        <div class="intro--content txt-shadow">
          <h2>上海市乡村振兴“三园工程”简介</h2>
          <p style="text-indent: 1.2vw;padding: 0 0.8vw">上海市乡村振兴战略，坚持面向全球、面向未来，以推进“三园工程”（以全面提升农村环境面貌为核心的“美丽家园”工程，以全面实现农业提质增效为核心的“绿色田园”工程，以全面促进农民持续增收为核心的“幸福乐园”工程）为重要抓手，争取到2022年，率先基本实现农业农村现代化。</p>
          <ul>
            <li>（一）“美丽家园”工程
              <ul>
                <li>实施“十百千”行动计划。到2022年，全市建设若干乡村振兴示范村、美丽乡村示范村，实现行政居环境整治全覆盖，形成一批可推广、可示范的乡村建设和发展模式。</li>
                <li>实施农居相对集中行动计划。加大推进农民向城镇集中居住力度，推进村落散户向经规划的农民集中居住点平移。</li>
              </ul>
            </li>
            <li>（二）“绿色田园”工程
              <ul>
                <li>实施都市现代绿色农业发展行动计划。建立以绿色生态为导向的制度体系，全面提升农业绿色生产技术和设施装备水平。
                </li>
                <li>实施构建现代农业经营体系行动计划。完善促进新型农业经营主体发展的制度体系，构建地产绿色农产品产销平台，创新经营模式。
                </li>
              </ul>
            </li>
            <li>
              （三）“幸福乐园”工程
              <ul>
                <li>实施农民长效增收行动计划。有针对性地对农民开展培训，促进农民非农就业，加快培育职业农民。发展新型集体经济，增加农民财产性收入。</li>
                <li>
                  实施农民美好生活提升行动计划。完善农村公共服务设施布局，提升养老、医疗、教育、文化等公共服务能力，加强和创新乡村治理。
                </li>
              </ul>
            </li>
          </ul>

        </div>
      </div>
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

        <div v-for="(item,idx) in words" :key="idx" class="sanyuan-bottom-content can-hover" @click="pushTo(item.link)">
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
      <div class="sanyuan-sidebar-head can-hover" @click="showIntroduction">
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
      { content: `美丽家园`, subtext: '——哈哈哈哈哈哈哈', link: 'https://www.baidu.com' },
      { content: '绿色田园', subtext: '——哈哈哈哈哈哈哈', link: 'https://www.baidu.com' },
      { content: '幸福乐园', subtext: '——哈哈哈哈哈哈哈', link: 'https://www.baidu.com' }
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
    pushTo (link) {
      if (window && window.location && link) {
        window.location.href = link
      }
    },
    showIntroduction () {
      this.$refs.modalContainer.style.transform = 'scale(1,1)'
    },
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
    },
    hideModal () {
      this.$refs.modalContainer.style.transform = 'scale(0,0)'
    }
  }
}
</script>

<style scoped>
  .introduction-modal {
    position: relative;
    width: 40%;
    height: 90%;
    /*background: black;*/
  }

  .introduction-modal .intro-border1 {
    position: absolute;
    top: 1%;
    left: 5%;
  }

  .introduction-modal .intro-border2 {
    top: 95%;
    right: 5%;
    rotation-point: 50% 50%;
    transform: rotate(180deg);
  }

  .introduction-modal .intro--content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 80%;
    height: 80%;
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-size: 0.6vw;
    line-height: 0.9vw;
  }
  .intro--content ul{
    padding: 0;
    margin: 0;
  }
  .intro--content ul li {
    list-style: none;
    line-height: 1vw;
    font-size: .8vw;
  }
  .intro--content ul li ul {
    padding-left: .7vw;
  }
  .intro--content ul li ul li{
    line-height: 1.2vw;
    font-size: 0.6vw;
    font-weight: lighter;
    list-style: disc;
    text-indent: 1.2vw;
    margin: 0.2vw 0;
  }
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

  .introduction-bg {
    background: url("../assets/Dark-Grey-Texture-Wallpaper-5.jpg");
    background-size: cover;
    opacity: .90;
    display: flex;
    justify-content: center;
    align-items: center;
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
