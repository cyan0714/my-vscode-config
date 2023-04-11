<template>
  <div class="el-dropdown-years">
    <div class="right-block-top-right common-block">
      <div class="cb-wrapper">
        <div class="cw-left">
          <img src="../../../imgs/dataAnalysis/title_3.png" />
          <span>2022年目标任务指标监控</span>
        </div>
        <el-dropdown trigger="click"
                     @command="handleCommand">
          <el-button class="cw-btn"
                     type="primary">
            <div>
              <span>{{ currentYear }}年</span>
              <i class="el-icon-caret-bottom"></i>
            </div>
          </el-button>
          <el-dropdown-menu slot="dropdown"
                            class="years-dropdown">
            <el-dropdown-item v-for="(year, index) in years"
                              :command="year">{{ year }}</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      currentYear: new Date().getFullYear(),
      years: []
    }
  },
  props: {},
  computed: {},
  created() {
    this.getYears()
  },
  mounted() { },
  methods: {
    handleCommand(command) {
      this.currentYear = command
    },
    getYears() {
      let year = new Date().getFullYear();
      for (let i = year - 10; i <= year + 10; i++) {
        this.years.push(i);
      }
    },
  }
}
</script>

<style scoped lang="scss">
.el-dropdown-years {
  .right-block-top-right {
    .cb-wrapper {
      display: flex;
      justify-content: space-between;

      .cw-left {
        display: flex;
        align-items: center;

        span {
          margin-left: 10px;
          font-weight: 700;
          color: #333;
          font-size: 18px;
        }
      }

      .cw-btn {
        background: #f2f6ff;
        padding: 8px 16px;
        color: #000;
        width: 109px;
        font-size: 15px;
        border: none;

        div {
          display: flex;
          justify-content: space-between;
          align-items: center;

          i {
            color: #487efa;
            font-style: 16px;
          }
        }
      }
    }
  }
}
</style>
