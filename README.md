# Algorithm Optimization Skill

中文算法与算子优化 skill，采用通用 `SKILL.md` 格式，附 Codex 元数据。适用于一般算法、CPU/GPU/LPU 算子及 FPGA/ASIC 软硬件优化。

核心是：**在前置条件和现有约束下，优先实现整体直接净收益最大的可行方案；围绕具体假设推进，并用足够的证据验证。**

## 安装

需要先具备此私有仓库的 GitHub 读取权限。Codex 可将仓库克隆到 skills 目录，安装目录名使用 `algorithm-optimization`：

```bash
git clone https://github.com/endlesshi/Algorithm-optimization-skill.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/algorithm-optimization"
```

如果已经在其他目录维护仓库，可将该目录链接到上述安装位置。目标已存在时先检查，不覆盖已有 skill。安装后开启新会话，让工具重新发现 skill。

其他支持 Skills 的工具：将仓库放入该工具指定的 skill 目录，使用 `SKILL.md` 入口；`agents/openai.yaml` 是可选的 Codex 元数据，核心流程不依赖它。

## 使用示例

```text
使用 $algorithm-optimization 分析这个算子为什么慢。
先从现有代码、测试和报告核实事实，按整体净收益排序候选，暂不改代码。
```

```text
使用 $algorithm-optimization 优化这个实现。
保持现有接口和精度标准，目标是给定输入分布的端到端延迟。
允许一个具体假设包含多处协同修改，记录每轮结果和停止依据。
```

```text
使用 $algorithm-optimization 检查这份优化报告。
核对模型周期、单算子实测与整模型吞吐的计时边界及基线，指出还缺哪些证据。
```

```text
使用 $algorithm-optimization 评估这个 ASIC 的吞吐瓶颈。
允许调整计算单元、SRAM bank 和流水结构；同时报告面积、功耗和可实现频率代价。
```

描述具体目标、工作负载、允许修改范围和验收要求会提高效果；已经能从项目查明的事实不必重复填写。默认允许自动发现，是否实施由用户请求范围决定。

## 内容导航

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | 入口、工作范围、执行闭环和按需读取导航 |
| [需求与基线](references/requirements-and-baselines.md) | 四类需求、六类约束、参考与基线角色 |
| [完整方法树](references/method-tree.md) | 算/存 × 工作需求、单次实现、资源组织、映射与调度、运行状态 |
| [测量与决策](references/measurement-and-decisions.md) | 指标边界、按需测量、诊断、排序、验证与停止 |
| [复现与交付](references/reproducibility-and-delivery.md) | 不可变版本、对象共享、证据保留、复现层级及模板用法 |
| [案例](references/cases.md) | Prefill、RMSNorm、Decode、其他平台及ASIC的机制与条件 |
| [实验记录模板](assets/experiment-manifest.json) | 可选JSON起点；不自动执行、不强制替换项目格式 |
| [交付模板](assets/delivery-template.md) | 版本、运行、结果、证据与恢复入口 |
| [验证记录](VALIDATION.md) | 结构检查、方法树保真、独立目录检查与情景走查 |

第一版提供流程、参考和模板，不包含构建器、硬件驱动、性能采集器或新的实验管理框架；使用所在项目已有工具。缺少工具或设备时记录影响，不把离线检查写成已完成上板。

## 来源与维护

依据用户提供的《算法算子优化方法总结.md》，2026-11-09版本：

```text
SHA256 c7c894bfec02fc0fa4b416ee01359ebae17451eeeb3533acf6e35e42f863cbcd
```

入口对应原文第一、三、七章；需求与基线对应第二、四章；方法树保留第六章的完整算/存子树与分类边界；测量与决策对应第五、七章；复现与模板对应第四章、交付部分和附录A/B；案例提炼自附录C/D。

源文档保持不变。本仓库包含经组织的指导内容，不包含原始工程、权重、板卡镜像或本机实验日志。案例中的历史数字有来源范围说明，不作为当前平台的测试结果。

更新方法时维护对应参考、模板及验证记录，避免入口和参考重复维护同一套细节。更新skill不表示重新验证了案例中的硬件性能。保留私有仓库设置；本次未额外指定开源许可证。
