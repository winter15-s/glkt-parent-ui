<template>
  <div class="dashboard-container">
    <div class="welcome-section">
      <h2 class="welcome-title">欢迎回来，{{ name }}</h2>
      <p class="welcome-desc">今天是 {{ currentDate }}，祝您工作愉快！</p>
    </div>

    <el-row :gutter="20" class="stat-cards">
      <el-col :span="6">
        <el-card shadow="hover" class="stat-card">
          <div class="stat-card__icon" style="background: #409eff;">
            <i class="el-icon-user"></i>
          </div>
          <div class="stat-card__content">
            <div class="stat-card__value">1,280</div>
            <div class="stat-card__label">用户总数</div>
          </div>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover" class="stat-card">
          <div class="stat-card__icon" style="background: #67c23a;">
            <i class="el-icon-order"></i>
          </div>
          <div class="stat-card__content">
            <div class="stat-card__value">3,650</div>
            <div class="stat-card__label">订单数量</div>
          </div>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover" class="stat-card">
          <div class="stat-card__icon" style="background: #e6a23c;">
            <i class="el-icon-money"></i>
          </div>
          <div class="stat-card__content">
            <div class="stat-card__value">¥ 89,520</div>
            <div class="stat-card__label">销售金额</div>
          </div>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover" class="stat-card">
          <div class="stat-card__icon" style="background: #f56c6c;">
            <i class="el-icon-chat-dot-round"></i>
          </div>
          <div class="stat-card__content">
            <div class="stat-card__value">568</div>
            <div class="stat-card__label">消息数量</div>
          </div>
        </el-card>
      </el-col>
    </el-row>

    <el-row :gutter="20" class="content-section">
      <el-col :span="16">
        <el-card class="recent-activity">
          <div slot="header" class="card-header">
            <span>最近活动</span>
          </div>
          <el-timeline>
            <el-timeline-item timestamp="2024-01-15 10:30" placement="top">
              <el-card shadow="never">
                <p>新用户 张三 完成注册</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2024-01-15 09:20" placement="top">
              <el-card shadow="never">
                <p>订单 #20240115001 已发货</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2024-01-14 16:45" placement="top">
              <el-card shadow="never">
                <p>系统完成日常备份</p>
              </el-card>
            </el-timeline-item>
          </el-timeline>
        </el-card>
      </el-col>
      <el-col :span="8">
        <el-card class="quick-links">
          <div slot="header" class="card-header">
            <span>快捷操作</span>
          </div>
          <div class="quick-links__list">
            <el-button type="primary" icon="el-icon-plus" class="quick-link-btn">新建课程</el-button>
            <el-button type="success" icon="el-icon-document" class="quick-link-btn">查看订单</el-button>
            <el-button type="warning" icon="el-icon-setting" class="quick-link-btn">系统设置</el-button>
            <el-button type="info" icon="el-icon-chat-line-round" class="quick-link-btn">消息中心</el-button>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name'
    ]),
    currentDate() {
      const options = { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' }
      return new Date().toLocaleDateString('zh-CN', options)
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    padding: 20px;
  }
}

.welcome-section {
  margin-bottom: 24px;
  padding: 20px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 8px;
  color: #fff;

  .welcome-title {
    font-size: 24px;
    margin: 0 0 8px 0;
  }

  .welcome-desc {
    font-size: 14px;
    margin: 0;
    opacity: 0.9;
  }
}

.stat-cards {
  margin-bottom: 20px;
}

.stat-card {
  .el-card__body {
    display: flex;
    align-items: center;
    padding: 20px;
  }

  &__icon {
    width: 56px;
    height: 56px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-right: 16px;

    i {
      font-size: 28px;
      color: #fff;
    }
  }

  &__content {
    flex: 1;
  }

  &__value {
    font-size: 24px;
    font-weight: bold;
    color: #303133;
    line-height: 1.2;
  }

  &__label {
    font-size: 14px;
    color: #909399;
    margin-top: 4px;
  }
}

.content-section {
  margin-top: 20px;
}

.card-header {
  font-size: 16px;
  font-weight: bold;
}

.recent-activity {
  min-height: 300px;
}

.quick-links {
  &__list {
    display: flex;
    flex-direction: column;
    gap: 12px;

    .quick-link-btn {
      width: 100%;
      margin-left: 0;
    }
  }
}
</style>
