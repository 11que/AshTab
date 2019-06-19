<template>
<!-- :style="'transform: translateX('+data.menuSize+'px);'" -->
  <div :class="['menu',{'active':data.active}]" :style="'background:'+data.menuRGB">
    <div class="set" @click="open">
      <span class="iconfont icon-setting"></span>
    </div>
    <div class="off" @click="open">
      <span class="iconfont icon-poweroff" v-show="data.active"></span>
    </div>
  </div>
</template>

<script>
export default {
  props:['status'],
  data () {
    return {
      data: {
        active: false,
        menuSize: 560,
        menuRGB: '#25272f',
      }
    };
  },

  components: {},

  computed: {},

  methods: {
    open() {
      this.data.active = !this.data.active;
      this.$emit('status', this.data)
    }
  }
}

</script>
<style lang='scss' scoped>

%ico {
  font-size: 45px;
  cursor: pointer;
  color: rgba(255, 255, 255, 0.445)
}

.menu {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  width: 560px;
  transform:translateX(560px);
  &:hover {
    background: #fff;
  }
  .set {
    position: absolute;
    top: 0;
    left: -50px;
    transition: all .4s;
    filter: blur(20px);
    &:hover {
      filter: blur(0px)
    }
    span {
      @extend %ico
    }
  }

  .off {
    position: absolute;
    top: 0;
    right: 5px;
    span {
      @extend %ico;
    }
  }
}

.menu.active {
  transform: translateX(0px);
}

@media (max-width: 800px) {
  .menu {
    width: 100vw;
    transform: translateX(101vw);
  }
} 
</style>