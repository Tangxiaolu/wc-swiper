<style>
  .btn {


    position: relative;
    /*display: inline-block;*/
    width: 50%;
    padding: 6px 12px;
    margin-bottom: 0;
    font-size: 14px;
    font-weight: 400;
    line-height: 1.42;
    color: #333;
    text-align: center;
    white-space: nowrap;
    vertical-align: top;
    cursor: pointer;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ccc;
    border-radius: 3px;
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
    border-bottom-right-radius: 3px;
    border-bottom-left-radius: 3px;
    color: #fff;
    background-color: #007aff;
    border: 1px solid #007aff;
    margin: 10px auto; 
  }
  .swiper {
    width: 100%;
    height: 300px;
  }
  .a {
    background: #123456;
  }
  .b {
    background: #674567;
  }
  .c {
    background: #445678;
  }
  .d {
    background: #689989;
  }
  .e {
    background: #333391;
  }
  .f {
    background: red;
  }
  .slide {
    font-size: 50px;
    display: flex;
    align-items:center;
    justify-content: center;
  }
  .text {
    margin: 10px;
  }
</style>
<template>
  <div class="container">
    <wc-swiper class="swiper" v-if="list.length" @transitionend="transitionend" ref="swiper"
      :defaultSlide="0" :interval="1500" :pagination="true">
        <wc-slide v-for="(v, k) in list" :key="k" :class="map[k]">
          {{v}}
        </wc-slide>
    </wc-swiper>  

    <div class="text">当前是第{{currentSlide}}个slide</div>  

    <div class="btn" @click="previous">上一个</div>
    <div class="btn" @click="next">下一个</div>


    <div class="btn" @click="slideTo">滚动到索引=3的</div>
  </div>

</template>
<script>

  export default {
    name: 'App',
    data () {
      return {
        list: [],
        map: {
          0: 'slide a',
          1: 'slide b',
          2: 'slide c',
          3: 'slide d',
          4: 'slide e',
          5: 'slide f'
        },
        currentSlide: 0
      }
    },
    mounted () {
      this.fetchList();
    },
    methods: {
      fetchList () {
        this.list = [0,1,2,3,4,5];
      },
      transitionend (current) {
        // console.log('')
        // console.log(current,'dangqin')
        this.currentSlide = current;
        document.querySelector('.text').innerHTML = '当前是第' + current + '个 slide';
      },
      previous () {
        this.$refs.swiper.previous();
      },
      next () {
        this.$refs.swiper.next();
      },
      slideTo () {
        this.$refs.swiper.slideTo(3);
      }
    }
  }
</script>