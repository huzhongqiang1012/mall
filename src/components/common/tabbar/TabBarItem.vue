<template>
  <!--所有的ITEM 都展示不同图片，不同文字-->
  <div class="tab-bar-item" @click="ItemClick">
    <div v-if="isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <div v-bind:style="activeSyle">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "TabBarItem",
    props: {
      path: String,
      activeColor: {
        type: String, // 类型
        default: '#9a9a9a',//默认文字颜色
      }
    },
    data() {
      return {
        // isActive: false
      }
    },
    computed: {
      // 那个路由活跃，那个显示
      isActive() {
        //  /home   ->   item1(/home)  = true
        //  /home   ->   item1(/category)  = false
        //  /home   ->   item1(/cart)  = false
        //  /home   ->   item1(/my)  = false
        // 当前路由  ===  当前路由中的link值  ?  true : Flase
        return this.$route.path.indexOf(this.path)
      },
      // 动态绑定样式，文字颜色
      activeSyle() {
        // 当前路由是否处于活跃？  true  : false
        return this.isActive ? {color: this.activeColor} : {}
      }
    },
    methods: {
      // 路由跳转，展示对应的组件
      ItemClick() {
        console.log(this.link);
        console.log(this.$route.path);
        //  $router.push  跳转路由,有返回功能
        //  $router.replace  跳转路由,没有返回功能
        this.$router.push(this.path)
      }
    }
  }
</script>

<style>

  .tab-bar-item {
    flex: 1;
    text-align: center;
    font-size: 14px;
  }

  .tab-bar-item img {
    width: 24px;
  }

  /*.active {*/
  /*  color: black;*/
  /*  font-weight: 500;*/
  /*}*/

</style>
