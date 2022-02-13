<template>
  <div>
    <el-card header="基本信息">
      <div slot="header" class="card-header-action">
        <span>基本信息</span>
        <div>
          <el-button type="primary" @click="handleSubmit">保存</el-button>
          <el-button type="danger">取消</el-button>
        </div>
      </div>
      <el-form label-width="80px" :model="form" inline>
        <el-form-item label="单据编号">
          <el-input v-model="form.code"></el-input>
        </el-form-item>
        <el-form-item label="业务类型">
          <el-select v-model="form.type" placeholder="请选择业务类型">
            <el-option label="报损处理" value="baosui"></el-option>
            <el-option label="调拨出库" value="diaobochuku"></el-option>
            <el-option label="其他出库" value="other"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="调出仓库">
          <el-select v-model="form.out" placeholder="请选择调出仓库">
            <el-option label="杭州总仓" value="hz"></el-option>
            <el-option label="温州仓库" value="wz"></el-option>
            <el-option label="江西仓库" value="jx"></el-option>
            <el-option label="河北仓库" value="hb"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="调入仓库">
          <el-select v-model="form.in" placeholder="请选择调入仓库">
            <el-option label="杭州总仓" value="hz"></el-option>
            <el-option label="温州仓库" value="wz"></el-option>
            <el-option label="江西仓库" value="jx"></el-option>
            <el-option label="河北仓库" value="hb"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="业务员">
          <el-input v-model="form.user"></el-input>
        </el-form-item>
        <el-form-item label="日期">
          <el-date-picker
            style="width: 178px;"
            v-model="form.date"
            type="date"
            placeholder="选择日期">
          </el-date-picker>
        </el-form-item>
      </el-form>
    </el-card>
    <el-card style="margin-top: 20px;">
      <div slot="header" class="card-header-table">
        <span>商品信息</span>
        <div class="card-header-table__actions">
          <i class="el-icon-circle-plus" @click="handleCreateRow"/>
        </div>
      </div>
      <el-table
        header-row-class-name="table-header-row"
        header-cell-class-name="table-header-row"
        :data="tableData"
        :current-row-key="1"
        stripe
        highlight-current-row
        style="width: 100%">
        <el-table-column
          prop="goods"
          label="商品"
          width="180"
        >
          <template slot-scope="scope">
            <span>{{ constants.goods[scope.row.goods] }}</span>
          </template>
        </el-table-column>
        <el-table-column
          prop="spec"
          label="规格"
          width="180"
        >
          <template slot-scope="scope">
            <span>{{ constants.spec[scope.row.spec] }}</span>
          </template>
        </el-table-column>
        <el-table-column
          prop="count"
          label="出库数量"
          width="180">
        </el-table-column>
        <el-table-column
          prop="store"
          label="库存"
          width="180">
        </el-table-column>
        <el-table-column
          label="更多操作"
          fixed="right"
        >
          <template>
            <el-button
              size="mini"
              type="default"
              @click="handleDelete(scope.$index, scope.row)"
            >
              编辑
            </el-button>
            <el-button
              size="mini"
              type="danger"
              @click="handleDelete(scope.$index, scope.row)"
            >
              删除
            </el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-card>
    <inventory-dialog
      :visible="dialog.visible"
      @close="handleCloseDialog"
      @confirm="handleDialogConfirm"
    />
  </div>
</template>
<script>
import { Card, Form, FormItem, Select, Option, Input, DatePicker, Table, TableColumn, Button, MessageBox, Message } from 'element-ui';
import InventoryDialog from '../../../components/inventory-dialog';

export default {
  components: {
    [Card.name]: Card,
    [Form.name]: Form,
    [FormItem.name]: FormItem,
    [Select.name]: Select,
    [Option.name]: Option,
    [Input.name]: Input,
    [DatePicker.name]: DatePicker,
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
    [Button.name]: Button,
    InventoryDialog
  },

  data () {
    return {
      form: {
        name: '',
        type: 'diaobochuku',
        user: '管理员 - xxx',
        out: 'hz',
        in: 'wz',
        date: Date.now()
      },
      tableData: [],
      dialog: {
        visible: false
      },
      constants: {
        goods: {
          baosui: '螺丝钉',
          diaobochuku: '塑胶泡沫',
          other: '车底板'
        },
        spec: {
          baosui: '个',
          diaobochuku: '包',
          other: '袋'
        }
      }
    };
  },

  methods: {
    // 添加一行
    handleCreateRow () {
      this.dialog = {
        visible: true
      };
    },

    // 关闭 dilaog
    handleCloseDialog () {
      this.dialog = {
        visible: false
      };
    },

    // dialog 保存
    handleDialogConfirm (data) {
      this.dialog = {
        visible: false
      };
      this.tableData.push(data);
    },

    // 提价
    handleSubmit () {
      MessageBox.confirm('是否确定「出库」操作', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      }).then(() => {
        Message.success('出库成功');
      });
    }
  }
};
</script>
<style lang="scss">
.card-header-action {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-header-table {
  display: flex;
  align-items: center;

  &__actions {
    margin-left: 20px;
    display: flex;
    align-items: center;

    & .el-icon-circle-plus {
      font-size: 24px;
      color: #5ba8ff;
      cursor: pointer;
    }
  }
}

.table-header-row {
  background-color: #f9f9f9 !important;
}
</style>
