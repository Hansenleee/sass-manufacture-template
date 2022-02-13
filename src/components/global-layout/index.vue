<template>
  <el-container style="height: 100%;">
    <el-aside width="200px">
      <layout-menu />
    </el-aside>
    <el-container>
      <el-header style="padding: 0;">
        <layout-header />
      </el-header>
      <el-main style="background: #eef0f3;"><slot /></el-main>
    </el-container>
  </el-container>
</template>
<script>
import { Container, Header, Aside, Main } from 'element-ui';
import Menu from './menu';
import LayoutHeader from './header';

export default {
  components: {
    [Container.name]: Container,
    [Header.name]: Header,
    [Aside.name]: Aside,
    [Main.name]: Main,
    'layout-menu': Menu,
    'layout-header': LayoutHeader
  }
};
</script>
<style lang="scss">
body {
  margin: 0;
  padding: 0;
  height: 100vh;

  & #app {
    height: 100%;
  }
}
</style>
