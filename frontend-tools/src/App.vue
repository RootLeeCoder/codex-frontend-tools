<script setup lang="ts">
import { ArrowRight } from '@element-plus/icons-vue'

type Tool = {
  name: string
  description: string
  url: string
  tags?: string[]
}

type ToolSection = {
  title: string
  description: string
  tools: Tool[]
}

const toolSections: ToolSection[] = [
  {
    title: '颜色与设计',
    description: '快速处理颜色编码、渐变与图标等设计工作常用的小工具。',
    tools: [
      {
        name: 'RGB 和 HEX 转换',
        description: '在不同颜色格式之间来回切换，方便拷贝配色。',
        url: 'https://www.colorhexa.com/',
        tags: ['颜色', '设计']
      },
      {
        name: '渐变背景生成器',
        description: '生成多种渐变背景并导出 CSS 代码。',
        url: 'https://cssgradient.io/',
        tags: ['CSS', '渐变']
      },
      {
        name: 'SVG 图标库',
        description: '查找和下载常用 SVG 图标素材。',
        url: 'https://www.iconfont.cn/',
        tags: ['SVG', '图标']
      }
    ]
  },
  {
    title: '数据格式化',
    description: '处理接口调试、数据清洗和转换时常用到的在线工具。',
    tools: [
      {
        name: 'JSON 格式化工具',
        description: '格式化、压缩与校验 JSON 数据结构。',
        url: 'https://jsonformatter.org/json-parser',
        tags: ['JSON', '格式化']
      },
      {
        name: '时间戳转换',
        description: '在 Unix 时间戳与可读时间之间快速互转。',
        url: 'https://tool.lu/timestamp/',
        tags: ['日期', '时间']
      },
      {
        name: 'Base64 编解码',
        description: '将文本、图片进行 Base64 编码或解码。',
        url: 'https://www.base64decode.org/',
        tags: ['编码', '文本']
      }
    ]
  },
  {
    title: '开发调试',
    description: '辅助定位问题、生成测试数据的效率工具。',
    tools: [
      {
        name: '正则表达式测试',
        description: '实时调试并解释正则表达式匹配结果。',
        url: 'https://regex101.com/',
        tags: ['正则', '调试']
      },
      {
        name: 'UUID 生成器',
        description: '生成唯一标识符，支持多种 UUID 版本。',
        url: 'https://www.uuidgenerator.net/',
        tags: ['UUID', '随机数']
      },
      {
        name: 'Cron 表达式助手',
        description: '在线生成与校验 Cron 定时表达式。',
        url: 'https://cron.qqe2.com/',
        tags: ['Cron', '定时任务']
      }
    ]
  }
]

const scrollToContent = () => {
  document.getElementById('tool-sections')?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}
</script>

<template>
  <div class="page">
    <header class="hero">
      <div class="hero__badge">Vue 3 · Element Plus · TypeScript</div>
      <h1>前端工具合集</h1>
      <p>
        精选覆盖颜色设计、数据格式化、开发调试等多个场景的在线工具导航，帮助你在实际项目中快速找到解决方案。
      </p>
      <el-button type="primary" size="large" @click="scrollToContent" :icon="ArrowRight">
        浏览工具目录
      </el-button>
    </header>

    <main id="tool-sections" class="content">
      <section v-for="section in toolSections" :key="section.title" class="content__section">
        <div class="section__header">
          <div>
            <h2>{{ section.title }}</h2>
            <p>{{ section.description }}</p>
          </div>
          <el-tag type="info">{{ section.tools.length }} 个工具</el-tag>
        </div>

        <div class="tool-grid">
          <el-card v-for="tool in section.tools" :key="tool.name" shadow="hover" class="tool-card">
            <div class="tool-card__header">
              <h3>{{ tool.name }}</h3>
              <div class="tool-card__tags">
                <el-tag v-for="tag in tool.tags" :key="tag" type="success" effect="light" round>
                  {{ tag }}
                </el-tag>
              </div>
            </div>
            <p class="tool-card__description">
              {{ tool.description }}
            </p>
            <div class="tool-card__footer">
              <el-button
                type="primary"
                text
                size="large"
                :icon="ArrowRight"
                tag="a"
                :href="tool.url"
                target="_blank"
                rel="noopener"
              >
                打开工具
              </el-button>
            </div>
          </el-card>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
.page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.hero {
  padding: 96px 24px 64px;
  text-align: center;
  background: radial-gradient(circle at top, rgba(64, 158, 255, 0.15), transparent 55%),
    linear-gradient(180deg, #f9fbff 0%, rgba(249, 251, 255, 0.6) 100%);
}

.hero__badge {
  display: inline-flex;
  align-items: center;
  padding: 8px 16px;
  border-radius: 999px;
  background: rgba(64, 158, 255, 0.1);
  color: #1f2937;
  font-weight: 600;
  font-size: 14px;
  margin-bottom: 24px;
}

.hero h1 {
  margin: 0 0 16px;
  font-size: 48px;
  font-weight: 700;
  color: #1f2937;
}

.hero p {
  max-width: 680px;
  margin: 0 auto 32px;
  font-size: 18px;
  color: #4b5563;
}

.content {
  flex: 1;
  padding: 0 24px 96px;
  max-width: 1040px;
  width: 100%;
  margin: 0 auto;
}

.content__section {
  margin-top: 64px;
}

.section__header {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 16px;
  margin-bottom: 24px;
}

.section__header h2 {
  margin: 0 0 8px;
  font-size: 28px;
  color: #1f2937;
}

.section__header p {
  margin: 0;
  color: #6b7280;
}

.tool-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
}

.tool-card {
  border: none;
  border-radius: 16px;
  background: #ffffff;
  box-shadow: 0 12px 40px rgba(64, 158, 255, 0.08);
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.tool-card__header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 12px;
}

.tool-card__header h3 {
  margin: 0;
  font-size: 20px;
  color: #1f2937;
}

.tool-card__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tool-card__description {
  margin: 0;
  color: #4b5563;
  line-height: 1.6;
  min-height: 60px;
}

.tool-card__footer {
  display: flex;
  justify-content: flex-end;
}

@media (max-width: 768px) {
  .hero {
    padding: 72px 16px 48px;
  }

  .hero h1 {
    font-size: 36px;
  }

  .hero p {
    font-size: 16px;
  }

  .section__header {
    flex-direction: column;
    align-items: flex-start;
  }

  .tool-card {
    padding: 20px;
  }
}
</style>
