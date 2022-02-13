<template>
  <el-dialog
    title="新增库存记录"
    :visible="visible"
    width="500px"
    :before-close="handleClose">
    <div>
      <el-form label-width="80px" :model="form" :rules="rules" ref="form">
        <el-form-item label="商品" prop="goods">
          <el-select style="width: 320px;" v-model="form.goods" placeholder="请选择商品">
            <el-option label="螺丝钉" value="baosui"></el-option>
            <el-option label="塑胶泡沫" value="diaobochuku"></el-option>
            <el-option label="车底板" value="other"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="规格" prop="spec">
          <el-select style="width: 320px;" v-model="form.spec" placeholder="请选择规格">
            <el-option label="个" value="baosui"></el-option>
            <el-option label="包" value="diaobochuku"></el-option>
            <el-option label="袋" value="other"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="出库数量">
          <el-input-number style="width: 320px;" v-model="form.count" :min="1" :max="99" />
        </el-form-item>
        <el-form-item label="库存">
          <el-input style="width: 320px;" v-model="form.store" disabled></el-input>
        </el-form-item>
      </el-form>
    </div>
    <span slot="footer" class="dialog-footer">
      <el-button @click="handleClose">取 消</el-button>
      <el-button type="primary" @click="handleConfirm">确 定</el-button>
    </span>
  </el-dialog>
</template>
<script>
import { Dialog, Form, FormItem, Button, Select, Option, InputNumber, Input } from 'element-ui';
import cloneDeep from 'lodash/cloneDeep';

export default {
  components: {
    [Dialog.name]: Dialog,
    [Button.name]: Button,
    [Form.name]: Form,
    [FormItem.name]: FormItem,
    [Select.name]: Select,
    [Option.name]: Option,
    [InputNumber.name]: InputNumber,
    [Input.name]: Input
  },

  props: {
    visible: Boolean
  },

  data () {
    return {
      form: {
        goods: '',
        spec: '',
        count: '',
        store: 99
      },
      rules: {
        goods: [
          { required: true, message: '请选择商品', trigger: 'blur' }
        ],
        spec: [
          { required: true, message: '请选择规格', trigger: 'blur' }
        ]
      }
    };
  },

  methods: {
    // 关闭
    handleClose () {
      this.$emit('close');
    },

    // 确定
    handleConfirm () {
      this.$refs.form.validate((valid) => {
        if (!valid) {
          return;
        }

        this.$emit('confirm', cloneDeep(this.form));
        this.$refs.form.resetFields();
      });
    }
  }
};
</script>
<style lang="scss" scoped>

</style>
