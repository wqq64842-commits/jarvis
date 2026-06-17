# 贡献指南

感谢你愿意为 **Jarvis-Mac** 出一份力！无论是修 Bug、加功能、写文档还是提建议，都非常欢迎。

## 🔒 第一条铁律：不要提交任何敏感信息

这是个语音助手项目，配置里有密钥。**提交前请务必确认没有夹带敏感文件**：

```bash
git ls-files | grep -Ei "api_key|base_url|^model\.txt$|^notes\.txt$|memory\.json|\.wav$|\.mp3$"
# 期望输出：空。如果有内容，说明 .gitignore 没挡住，停下来检查！
```

- 真实的 `api_key.txt` / `base_url.txt` / `model.txt` / `notes.txt` / `memory.json` 和音频样本都已被 `.gitignore` 排除。
- 仓库里只放 `*.example` 模板，绝不要把真实密钥写进示例文件再提交。

## 🛠️ 开发环境

```bash
git clone https://github.com/wqq64842-commits/jarvis-mac.git
cd jarvis-mac
python3.12 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp base_url.txt.example base_url.txt   # 填你自己的中转站
cp api_key.txt.example  api_key.txt
cp model.txt.example    model.txt
```

- 验证大脑连通：`./.venv/bin/python test_llm.py`
- 跑起来：`./run.sh`（带桌宠）或 `./run.sh --no-pet`（纯命令行）
- 仅限 **macOS**，需要 Python 3.12 与麦克风权限。

## 📐 代码风格

- 遵循现有风格：模块短小、职责单一，注释用中文、贴近周围代码的密度。
- 新功能尽量做成**工具**（见 `jarvis/tools.py`），让大模型可以调用。
- 改了桌宠（`jarvis/pet.py`）可以离屏渲染一帧自测，不必每次都开 GUI。
- 不引入重依赖；能用标准库解决就用标准库（本项目大模型调用即用 `urllib`）。

## 🔀 提交流程

1. Fork 本仓库，从 `main` 切出特性分支：`git checkout -b feat/你的功能`
2. 提交信息写清楚“做了什么、为什么”。
3. **推送前跑一遍上面的红线检查**，确认无敏感文件。
4. 发起 Pull Request，描述变更动机与测试方式。

## 🐛 提 Issue

用 [Issue 模板](.github/ISSUE_TEMPLATE) 提交 Bug 或功能建议。Bug 请附上：macOS 版本、Python 版本、复现步骤、相关日志（**记得抹掉日志里的密钥**）。

谢谢你，一起把贾维斯调教得更聪明 🤖
