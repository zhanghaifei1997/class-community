<template>
  <div class="card-wrap">
    <div class="card-tag">
      <i class="el-icon-caret-right"></i>
      <span v-if="ismanagement">我的创建<span class="color-block"></span>{{name}}</span>
      <span v-else>我的加入<span class="color-block"></span>{{name}}</span>
    </div>
    <div class="card-router">
      <el-row
        type="flex"
        justify="flex-left"
      >

        <el-col
          :span="8"
          class="icon-btn"
        >
          <a
            href="javascript:;"
            @click="toClassNotice"
          >
            <span>
              <svg-icon icon-class="message"></svg-icon>
            </span>
            <p>班级公告</p>
          </a>
        </el-col>
        <el-col
          :span="8"
          class="icon-btn"
        >
          <a
            href="javascript:;"
            @click="toClassAlbum"
          >
            <span>
              <svg-icon icon-class="picture"></svg-icon>
            </span>
            <p>班级相册</p>
          </a>
        </el-col>
        <el-col
          :span="8"
          class="icon-btn"
        >
          <a
            href="javascript:;"
            @click="toClassLeave"
          >
            <span>
              <svg-icon icon-class="leaveword"></svg-icon>
            </span>
            <p>班级留言</p>
          </a>
        </el-col>

      </el-row>
      <el-row
        type="flex"
        justify="flex-left"
      >
        <el-col
          :span="8"
          class="icon-btn"
        >
          <a
            href="javascript:;"
            @click="toClassMember"
          >
            <span>
              <svg-icon icon-class="member"></svg-icon>
            </span>
            <p>班级成员</p>
          </a>
        </el-col>
        <el-col
          :span="8"
          v-if="power>1"
          class="icon-btn"
        >
          <a
            href="javasript:;"
            @click="toFeature"
          >
            <span>
              <svg-icon icon-class="upload"></svg-icon>
            </span>
            <p>发布风采</p>
          </a>
        </el-col>
        <el-col
          v-if="ismanagement"
          :span="8"
          class="icon-btn"
        >
          <a
            href="javasript:;"
            @click.prevent="toPowerCheck">
            <span>
              <svg-icon icon-class="check"></svg-icon>
            </span>
            <p>权限审核</p>
          </a>
        </el-col>
        <el-col
          v-else
          :span="8"
          class="icon-btn"
        >
          <a
            href="javasript:;"
            @click.prevent="toPowerApply">
            <span>
              <svg-icon icon-class="apply"></svg-icon>
            </span>
            <p>申请权限</p>
          </a>
        </el-col>

      </el-row>
    </div>
    <el-dialog
      title="权限审核"
      :visible.sync="ifCheckPowerShow"
    >
      <power-check
        v-if="ifCheckPowerShow"
        :class_id="id"
        :class_name="name"
      ></power-check>
    </el-dialog>
    <el-dialog
      title="申请权限"
      :visible.sync="ifPowerAplyShow"
    >
      <power-apply
        v-if="ifPowerAplyShow"
        :class_id="id"
        :class_name="name"
      ></power-apply>
    </el-dialog>
  </div>
</template>

<script>
import PowerApply from '@/components/popdialog/PowerApply.vue'
import PowerCheck from '@/components/popdialog/PowerCheck.vue'
export default {
  data () {
    return {
      ifCheckPowerShow: false,
      ifPowerAplyShow: false
    }
  },
  methods: {
    toFeature () {
      this.$router.push({
        name: 'CreateFeature',
        params: { class_id: this.id }
      })
    },
    toClassAlbum () {
      this.$router.push({
        name: 'ClassAlbum',
        params: { class_id: this.id }
      })
    },
    toClassNotice () {
      this.$router.push({
        name: 'ClassNotice',
        params: { class_id: this.id }
      })
    },
    toClassLeave () {
      this.$router.push({
        name: 'ClassLeave',
        params: { class_id: this.id }
      })
    },
    toClassMember () {
      this.$router.push({
        name: 'ClassMember',
        params: { class_id: this.id }
      })
    },
    toPowerCheck () {
      this.ifCheckPowerShow = true
    },
    toPowerApply () {
      this.ifPowerAplyShow = true
    }
  },
  props: ['ismanagement', 'power', 'id', 'name'],
  components: {
    'power-apply': PowerApply,
    'power-check': PowerCheck
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/styles/mixin.scss';
.card-wrap {
  border: 1px solid #ccc;
  margin-bottom: 14px;
  .color-block {
    border: 2px solid #00bbdd;
  }
  .card-tag {
    @include flexSet($justify: flex-start, $align: center);
    height: 36px;
    border-bottom: 1px solid #ccc;
    span {
      font-size: 14px;
      margin: 0 4px;
    }
  }
  .card-router {
    .icon-btn {
      text-align: center;
      padding: 10px 0;
      a {
        color: #2e3135;

        span {
          font-size: 24px;
        }
        p {
          font-size: 14px;
          margin: 0;
          padding: 6px 0;
          &:hover {
            color: #00bbdd;
          }
        }
      }
    }
  }
}
</style>
<style lang="scss">
.card-tag {
  i {
    font-size: 20px;
  }
}
</style>
