<template>
  <div class="sh-search">
    <div class="sh-top">
      <span class="title"></span>
      <input type="text" v-model="inputText" :placeholder="engin" @keyup.enter='show($event)'>
      <!-- <a :href="'https://www.baidu.com/s?ie=UTF-8&wd='+sha">se</a> -->
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      sha: '',//搜索关键词
      engin: 'Baidu',
      inputText: '',
      text: '',
      nowIndex: -1,
      result: []
    };
  },

  components: {},

  computed: {},

  methods: {
    search(i) {
      window.location.href = 'https://www.baidu.com/s?ie=UTF-8&wd='+this.sha
    },
    show: function(ev) {
      // if (ev.keyCode == 38 || ev.keyCode == 40) {
      //   if (this.nowIndex < -1){
      //     return;
      //   }
      //   if (this.nowIndex != this.result.length && this.nowIndex != -1) {
      //     this.inputText = this.result[this.nowIndex];
      //   }
      //   return;
      // }
      // if (ev.keyCode == 13) {
      //   window.open('https://www.baidu.com/s?wd=' + this.inputText, '_blank');
      //   this.inputText = '';
      // }
      // this.text = this.inputText;
      // this.$http.jsonp('https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su', {
      //   params: {
      //       wd: this.inputText
      //   },
      //   jsonp: 'cb'
      // }).then(res => {
      //   this.result = res.data.s;
      // })
      window.open('https://www.baidu.com/s?wd=' + this.inputText, '_top')
    }
  }
}

</script>
<style lang='scss' scoped>
.sh-top {
  display: flex;
  flex-direction: column;
  text-align: center;
  input {
    padding: 5px 10px;
    font-size: 28px;
    border: 0;
    width: 100%;
    color: aliceblue;
    background: transparent;
    border-bottom: 1px solid rgba(255, 255, 255, 0.295);
    cursor: text;//指针变化
    outline: none;
    &:hover {
      border-bottom: 1px solid #fff;
    }
    &::-webkit-input-placeholder {
      color: rgba(255, 255, 255, .6);

    }
  }
}

.shfont {
  .shfont-model-color {
    input {
      &::-webkit-input-placeholder {
        color: #fff
      }
    }
  }

}
</style>