<template>
  <div class="menu-container">
    <div class="menu-container__header">
      <img src="https://gw.alipayobjects.com/zos/rmsportal/KDpgvguMpGfqaHPjicRK.svg" />
      <span>乐清兢业电子</span>
    </div>
    <el-menu
      style="width: 100%;"
      background-color="#001525"
      text-color="rgba(255, 255, 255, 0.8)"
      default-active="/inventory/out"
      :collapse="false"
      router
    >
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-s-goods"></i>
          <span>库存管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="/inventory/out">综合出库</el-menu-item>
          <el-menu-item index="/inventory/in">综合入库</el-menu-item>
          <el-menu-item index="/inventory/query">库存查询</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-s-finance"></i>
          <span>财务处理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="2-1">明细账</el-menu-item>
          <el-menu-item index="2-2">总分账</el-menu-item>
          <el-menu-item index="2-3">财务报表</el-menu-item>
          <el-menu-item index="2-4">费用明细表</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="3">
        <template slot="title">
          <i class="el-icon-s-order"></i>
          <span>基础资料</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="3-1">商品信息</el-menu-item>
          <el-menu-item index="3-2">计量单位</el-menu-item>
          <el-menu-item index="3-3">库存信息</el-menu-item>
          <el-menu-item index="3-4">客户信息</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="4">
        <template slot="title">
          <i class="el-icon-menu"></i>
          <span>系统设置</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="4-1">员工设置</el-menu-item>
          <el-menu-item index="4-2">操作日志</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
    </el-menu>
  </div>
</template>
<script>
import { Menu, Submenu, MenuItemGroup, MenuItem } from 'element-ui';

export default {
  components: {
    [Menu.name]: Menu,
    [Submenu.name]: Submenu,
    [MenuItem.name]: MenuItem,
    [MenuItemGroup.name]: MenuItemGroup
  }
};
</script>

<style lang="scss" scoped>
.menu-container {
  background: #001525;
  color: #fff;
  height: 100%;

  &__header {
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;

    & > img {
      width: 32px;
      height: 32px;
      margin-right: 10px;
    }
  }
}
</style>
