<template>
  <div>
    <div class="layout">
      <Topnav toggleMenuButtonVisible class="nav" />
      <div class="content">
        <aside v-if="menuVisible">
          <h2>文档</h2>
          <ol>
            <li>
              <router-link to="/doc/intro">介绍</router-link>
            </li>
            <!-- <li>
              <router-link to="/doc/install">安装</router-link>
            </li>
            <li>
              <router-link to="/doc/get-started">开始使用</router-link>
            </li> -->
          </ol>
          <h2>组件列表</h2>
          <ol>
            <li>
              <router-link to="/doc/switch">Switch</router-link>
            </li>
            <li>
              <router-link to="/doc/button">Button</router-link>
            </li>
            <li>
              <router-link to="/doc/dialog">Dialog</router-link>
            </li>
            <li>
              <router-link to="/doc/tabs">Tabs</router-link>
            </li>
            <li>
              <router-link to="/doc/message">Message</router-link>
            </li>
            <li><span>持续更新...</span></li>
          </ol>
        </aside>
        <main>
          <router-view></router-view>
        </main>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { inject, Ref } from 'vue';
import Topnav from '../components/Topnav.vue';

export default {
  components: { Topnav },
  setup() {
    const menuVisible = inject<Ref<boolean>>('menuVisible'); // get
    return { menuVisible };
  }
};
</script>

<style lang="scss" scoped>
$aside-index: 10;

.layout {
  display: flex;
  flex-direction: column;
  height: 100vh;
  > .nav {
    flex-shrink: 0;
  }
  > .content {
    flex-grow: 1;
    padding-top: 60px;
    padding-left: 156px;
    @media (max-width: 500px) {
      padding-left: 0;
    }
  }
}
.content {
  display: flex;
  > aside {
    flex-shrink: 0;
  }
  > main {
    flex-grow: 1;
    padding: 16px 30px;
    background: white;
  }
}
aside {
  background-color: #f9f9f9;
  // width: 150px;
  width: 170px;
  padding: 16px 0;
  position: fixed;
  top: 0;
  left: 0;
  padding-top: 70px;
  height: 100%;
  padding-top: 70px;
  z-index: $aside-index;

  > h2 {
    margin-bottom: 4px;
    padding: 0 16px;
  }
  > ol {
    > li {
      > a,
      span {
        padding: 4px 16px;
        display: block;
        text-decoration: none;
      }
      .router-link-active {
        color: white;
        background: #9dbf73;
      }
    }
  }
  main {
    overflow: auto;
  }
}
</style>
