<template>
  <div class="sh-time">
    <div class="mode-default size-big shadow"
     :style="{'transform':'translate(' + x +'px, ' + y +'px)'}">
      <!-- <span class="show">{{showTime}}</span> -->
      <span class="show" v-if="true" >
        {{showTime.slice(0,5)}}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      time: {
        mod:'mod1',
        start: '',
      },// 时间初始化
      x: 0,
      y: 0,
    };
  },

  components: {},

  computed: {
    showTime() {
      let i = String(this.time);
      let mod1 = ':';
      let mod2 = '-';
      let mod3 = '.';
      let mod0 = '';
      return i.slice(0, 2)+mod1+i.slice(2, 4)+mod1+i.slice(-2)
      // return i
    }
  },

  methods: {
    add(a, b) {
      //补0 
      return a + ('0' + b).slice(-2)
    },

    getDate() {
      this.weekday = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
      let isdate = new Date();
      let year = isdate.getFullYear();
      let month = isdate.getMonth() + 1;
      let date = isdate.getDate();
      let day = isdate.getDay();
      let hour = isdate.getHours();
      let minute = isdate.getMinutes();
      let second = isdate.getSeconds();
      let time = [hour, minute, second];
      return time.reduce(this.add,"")
    }
  },
  created() {
    const _this = this
    _this.time = _this.getDate()
    setInterval(() => {
      _this.time = _this.getDate()
    }, 1000);
  },

  mounted() {
    document.onmousemove = () => {
      let width = document.body.clientWidth / 40
      let height = document.body.clientHeight / 40
      this.x = event.pageX / 20 - width ;
      this.y = event.pageY / 20 - height;
    }
  }
}

</script>
<style lang='scss' scoped>
.sh-time {
  span {
    font-family: -apple-system, BlinkMacSystemFont, "Neue Haas Grotesk Text Pro", "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-weight: 500;
    cursor:default;//指针变化
    letter-spacing: 0.01em;//文字间隔
  }
  div {
    transition: cubic-bezier(0.075, 0.82, 0.165, 1);
  }

  .shadow {
    text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5)
  }

  .size-big {
    font-size: 150px
  }

  .size-default {
    font-size: 120px;
  }
  
//mode 字體選項
  .mode-default {
    .show {
      color:aliceblue;
    }
  }

//文字透明 + 字体边框
  .mode-stroke {
    color: transparent;
    -webkit-text-stroke: 1.5px #fedfe1;
  }
}

@media (max-width: 800px) {
  .sh-time {
    transform: scale(.8)
  }
}

@media (max-width: 400px) {
  .sh-time {
    transform: scale(.6);
  }
}
</style>