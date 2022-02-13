<template>
  <div class="header-container">
    <div class="header-container__left">
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
        <el-breadcrumb-item>库存管理</el-breadcrumb-item>
        <el-breadcrumb-item>综合出库</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="header-container__right">
      <i class="el-icon-search" />
      <i class="el-icon-chat-line-round" />
      <i class="el-icon-news" />
      <div class="user-info">
        <img src="https://gw.alipayobjects.com/zos/rmsportal/BiazfanxmamNRoxxVxka.png" />
        <span>系统超级管理员</span>
      </div>
    </div>
  </div>
</template>
<script>
import { Breadcrumb, BreadcrumbItem } from 'element-ui';

export default {
  components: {
    [Breadcrumb.name]: Breadcrumb,
    [BreadcrumbItem.name]: BreadcrumbItem
  }
};
</script>
<style lang="scss" scoped>
.header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  height: 100%;
  padding: 0 20px;
  box-shadow: 0 1px 4px rgba(0,21,41,.08);

  &__left {
    display: flex;
    align-items: center;
  }

  &__right {
    display: flex;
    align-items: center;
    justify-content: center;

    & > i {
      width: 38px;
    }

    & .user-info {
      display: flex;
      color: #333;
      font-size: 14px;
      align-content: center;

      & > img {
        width: 24px;
        margin-right: 10px;
      }
    }
  }
}
</style>
