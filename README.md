# Seven-Layer Visual Director

一个面向图片与视频生成提示词的原创 Codex Skill。它通过七层结构拆分视觉需求，明确参考图职责、固定项、允许变化、动作连续性与负面护栏，减少因信息混杂造成的反复抽卡。

## 七层结构

1. 场景密度
2. 成像方式
3. 妆造锚点
4. 动作骨架
5. 有控制的随机
6. 元素互认
7. 负面护栏

## 适用场景

- 从零编写图片或视频生成提示词
- 按参考图重构画面，同时分离身份、姿势、构图和风格职责
- 处理“只换脸”“保持结构不变”等局部编辑请求
- 规划视频首尾帧、镜头时间表与跨帧连续性
- 在迭代时只修改受影响层，保留其余已确认内容

## 安装

将本仓库安装到 Codex 的用户级 Skills 目录：

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo SilasMaker/seven-layer-visual-director \
  --path . \
  --name seven-layer-visual-director
```

安装后重启 Codex。

## 使用

在 Codex 中调用：

```text
$seven-layer-visual-director
```

新任务会先询问图片或视频模式，并返回对应的完整七层空白模板。若你已经提供了充分信息，Skill 会直接整理七层、检查冲突并输出可复制的完整提示词。

## 文件结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── image-template.md
    ├── video-template.md
    ├── method-notes.md
    └── output-contract.md
```

## 边界

- 本 Skill 负责整理与编译提示词，不直接调用图片或视频生成工具。
- 不承诺零抽卡、固定成功率、绝对锁脸或像素级复刻。
- 工具参数无法核实时，只给通用建议，不虚构模型、按钮或数值范围。

## 原创与许可

七层视觉结构及本 Skill 的方法设计为原创内容。项目采用 [MIT License](LICENSE)。
