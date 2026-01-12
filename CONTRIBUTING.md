<!-- 
  ⚠️ 使用说明 | Instructions:
  请根据实际情况更新联系方式和链接 | Please update contact info and links as needed
-->

# 贡献指南 | Contributing Guide

感谢你有兴趣为 XMU RCS Vision 做出贡献！本指南将帮助你快速上手，了解如何为我们的项目做出贡献。

## 📋 目录 | Table of Contents

- [行为准则](#行为准则--code-of-conduct)
- [如何开始](#如何开始--getting-started)
- [贡献方式](#贡献方式--ways-to-contribute)
- [开发流程](#开发流程--development-workflow)
- [代码规范](#代码规范--coding-standards)
- [提交规范](#提交规范--commit-guidelines)
- [Pull Request 流程](#pull-request-流程--pull-request-process)
- [问题报告](#问题报告--reporting-issues)

---

## 🤝 行为准则 | Code of Conduct

我们致力于为所有人提供一个友好、安全和包容的环境。参与本项目即表示你同意遵守以下准则：

- ✅ **尊重他人**：尊重不同的观点和经验
- ✅ **建设性反馈**：提供有益的、建设性的反馈
- ✅ **专注于最佳方案**：为项目和社区寻求最佳解决方案
- ✅ **展现同理心**：理解并尊重他人的处境和感受
- ❌ **不容忍骚扰**：任何形式的骚扰行为都不被接受

---

## 🚀 如何开始 | Getting Started

### 1. 环境准备

首先，确保你的开发环境满足以下要求：

#### 通用要求
- **Git** - 版本控制系统
- **GitHub账号** - 用于 fork 和 PR
- **代码编辑器** - 推荐 VS Code 或 CLion

#### 项目特定要求（根据不同项目选择）

**C++ 项目：**
- C++14 或更高版本
- CMake 3.10+
- OpenCV 4.x
- Qt 5.x（如果需要GUI）

**Python 项目：**
- Python 3.8+
- pip 或 conda
- virtualenv 或 venv

**前端项目：**
- Node.js 14+
- npm 或 yarn

### 2. Fork 和 Clone

```bash
# 1. Fork 项目到你的 GitHub 账号

# 2. Clone 你的 fork 到本地
git clone https://github.com/YOUR_USERNAME/PROJECT_NAME.git
cd PROJECT_NAME

# 3. 添加上游仓库
git remote add upstream https://github.com/XMURCSVision/PROJECT_NAME.git

# 4. 验证远程仓库
git remote -v
```

### 3. 安装依赖

根据项目类型，运行相应的安装命令：

**C++ 项目：**
```bash
mkdir build && cd build
cmake ..
make
```

**Python 项目：**
```bash
# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 安装依赖
pip install -r requirements.txt
pip install -r requirements-dev.txt  # 开发依赖
```

**前端项目：**
```bash
npm install
```

---

## 💡 贡献方式 | Ways to Contribute

你可以通过多种方式为项目做出贡献：

### 📝 1. 文档改进
- 修正拼写错误或不准确的描述
- 改进现有文档的清晰度
- 添加缺失的文档或示例
- 翻译文档到其他语言

### 🐛 2. 报告问题
- 报告 bug 或错误
- 提出新功能建议
- 询问使用问题

### 💻 3. 代码贡献
- 修复已知的 bug
- 实现新功能
- 优化性能
- 重构代码

### 🎨 4. 设计贡献
- UI/UX 设计改进
- 图标和视觉资源
- 品牌和宣传材料

### 🧪 5. 测试
- 编写单元测试
- 进行集成测试
- 性能测试
- 用户测试反馈

---

## 🔄 开发流程 | Development Workflow

### 1. 保持同步

在开始开发前，确保你的代码是最新的：

```bash
# 获取上游最新代码
git fetch upstream

# 切换到主分支
git checkout main

# 合并上游更新
git merge upstream/main

# 推送到你的 fork
git push origin main
```

### 2. 创建功能分支

```bash
# 创建并切换到新分支
git checkout -b feature/your-feature-name

# 分支命名规范：
# - feature/xxx  : 新功能
# - fix/xxx      : Bug 修复
# - docs/xxx     : 文档更新
# - refactor/xxx : 代码重构
# - test/xxx     : 测试相关
```

### 3. 开发和测试

```bash
# 进行开发...

# 运行测试
make test          # C++ 项目
pytest             # Python 项目
npm test           # 前端项目

# 运行代码检查
make lint          # C++ 项目
flake8 .           # Python 项目
npm run lint       # 前端项目
```

### 4. 提交更改

```bash
# 查看修改
git status
git diff

# 添加文件
git add .

# 提交（遵循提交规范）
git commit -m "feat: add new feature description"

# 推送到你的 fork
git push origin feature/your-feature-name
```

---

## 📐 代码规范 | Coding Standards

### C++ 代码规范

遵循 [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)：

```cpp
// 命名规范
class VisionDetector {  // 类名：大驼峰
public:
    void processImage();  // 方法名：小驼峰
    
private:
    int frame_count_;     // 成员变量：小写+下划线+后缀_
    static const int kMaxFrames = 100;  // 常量：k前缀+大驼峰
};

// 注释
/**
 * @brief 处理输入图像
 * @param image 输入的 cv::Mat 图像
 * @return 处理结果
 */
bool processImage(const cv::Mat& image);
```

### Python 代码规范

遵循 [PEP 8](https://pep8.org/)：

```python
# 命名规范
class VisionDetector:  # 类名：大驼峰
    def __init__(self):
        self.frame_count = 0  # 实例变量：小写+下划线
        self._private_var = None  # 私有变量：下划线前缀
    
    def process_image(self, image):  # 方法名：小写+下划线
        """处理输入图像
        
        Args:
            image: 输入的 numpy 数组图像
            
        Returns:
            处理结果
        """
        pass

# 常量：全大写+下划线
MAX_FRAMES = 100
```

### TypeScript/JavaScript 代码规范

遵循 [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)：

```typescript
// 命名规范
class VisionDetector {  // 类名：大驼峰
    private frameCount: number = 0;  // 私有变量：小驼峰
    
    public processImage(image: ImageData): boolean {  // 方法名：小驼峰
        // 实现
        return true;
    }
}

// 常量：全大写+下划线
const MAX_FRAMES = 100;

// 函数名：小驼峰
function processImage(image: ImageData): boolean {
    // 实现
    return true;
}
```

### 通用规范

- ✅ 使用有意义的变量名和函数名
- ✅ 保持函数简洁，单一职责
- ✅ 添加必要的注释，解释复杂逻辑
- ✅ 代码格式化要一致
- ✅ 删除调试代码和 console.log
- ✅ 处理错误和边界情况

---

## 📝 提交规范 | Commit Guidelines

我们使用 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

### 提交格式

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type 类型

- `feat`: 新功能
- `fix`: Bug 修复
- `docs`: 文档更新
- `style`: 代码格式（不影响代码运行）
- `refactor`: 重构（既不是新功能也不是修复）
- `perf`: 性能优化
- `test`: 测试相关
- `chore`: 构建过程或辅助工具的变动
- `ci`: CI 配置文件和脚本的变动

### 示例

```bash
# 简单提交
git commit -m "feat: add object tracking algorithm"

# 详细提交
git commit -m "fix: resolve camera calibration issue

- Fixed distortion coefficient calculation
- Updated calibration pattern detection
- Added unit tests for calibration module

Closes #123"
```

---

## 🔍 Pull Request 流程 | Pull Request Process

### 1. 创建 Pull Request

在 GitHub 上创建 PR 时，请：

- ✅ 使用清晰的标题描述你的更改
- ✅ 在描述中详细说明：
  - 解决了什么问题
  - 如何解决的
  - 是否有破坏性更改
  - 测试方法
- ✅ 关联相关的 issue（如 `Closes #123`）
- ✅ 添加截图或视频（如果是 UI 更改）

### 2. PR 模板

```markdown
## 描述 | Description
简要描述这个 PR 的内容

## 类型 | Type
- [ ] Bug 修复
- [ ] 新功能
- [ ] 文档更新
- [ ] 代码重构
- [ ] 性能优化

## 更改内容 | Changes
- 更改 1
- 更改 2
- 更改 3

## 测试 | Testing
描述如何测试这些更改

## 截图 | Screenshots
如果适用，添加截图

## 相关 Issue | Related Issues
Closes #123
```

### 3. Code Review

- PR 会由团队成员进行审查
- 请及时回应审查意见
- 根据反馈进行必要的修改
- 保持讨论专业和建设性

### 4. 合并

- 所有审查通过后
- CI 测试全部通过后
- 维护者会合并你的 PR
- 你的贡献会出现在下一个版本中

---

## 🐛 问题报告 | Reporting Issues

### Bug 报告

提交 bug 报告时，请包含：

```markdown
## 问题描述
清晰简洁地描述问题

## 复现步骤
1. 执行 '...'
2. 点击 '...'
3. 看到错误

## 期望行为
描述你期望发生什么

## 实际行为
描述实际发生了什么

## 环境信息
- OS: [e.g., Ubuntu 20.04]
- Python/C++/Node 版本:
- 项目版本:
- 其他相关信息:

## 截图
如果适用，添加截图

## 附加信息
任何其他有助于解决问题的信息
```

### 功能请求

提交功能请求时，请包含：

```markdown
## 功能描述
清晰简洁地描述你想要的功能

## 问题背景
这个功能解决了什么问题？

## 建议方案
你认为应该如何实现？

## 替代方案
是否考虑过其他替代方案？

## 附加信息
任何其他有助于理解需求的信息
```

---

## 🎓 学习资源 | Learning Resources

### 新手入门

- [Git 基础教程](https://git-scm.com/book/zh/v2)
- [GitHub 工作流](https://guides.github.com/introduction/flow/)
- [Markdown 语法](https://www.markdownguide.org/)

### 技术文档

- [OpenCV 文档](https://docs.opencv.org/)
- [PyTorch 教程](https://pytorch.org/tutorials/)
- [ROS 教程](http://wiki.ros.org/cn/ROS/Tutorials)

### 团队资源

- [官方文档](https://github.com/XMURCSVision/docs)
- [常见问题](https://github.com/XMURCSVision/docs/wiki/FAQ)
- [视频教程](https://space.bilibili.com/YOUR_BILIBILI_ID)

---

## 💬 获取帮助 | Getting Help

如果你在贡献过程中遇到问题，可以通过以下方式获取帮助：

- 💬 在相关 issue 或 PR 中评论
- 📧 发送邮件到 xmurcsvision@example.com
- 👥 加入 QQ 群：123456789
- 📺 观看 Bilibili 视频教程

---

## 🙏 致谢 | Acknowledgments

感谢所有为 XMU RCS Vision 做出贡献的开发者！你们的每一个贡献，无论大小，都让项目变得更好。

<div align="center">

**让我们一起用代码改变世界！**

Made with ❤️ by XMU RCS Vision Team

</div>
