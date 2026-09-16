<!--VITE PLUS START-->

# Using Vite+, the Unified Toolchain for the Web

This project is using Vite+, a unified toolchain built on top of Vite, Rolldown, Vitest, tsdown, Oxlint, Oxfmt, and Vite Task. Vite+ wraps runtime management, package management, and frontend tooling in a single global CLI called `vp`. Vite+ is distinct from Vite, and it invokes Vite through `vp dev` and `vp build`. Run `vp help` to print a list of commands and `vp <command> --help` for information about a specific command.

Docs are local at `node_modules/vite-plus/docs` or online at https://viteplus.dev/guide/.

## Built-in Commands vs Scripts

`vp <name>` runs a built-in command. `vp run <name>` runs a `package.json` script or a `vite.config.ts` task. Scripts cannot overwrite built-ins, so `vp dev` and `vp run dev` may do different things. Check `package.json` and `vite.config.ts` first, and run `vp run <name>` when the project defines a script or task with that name.

## Tool Versions

Run `vp toolchain` to show versions and relationships in the active Vite+
release. Add a tool name to select part of the graph. For example, run
`vp toolchain vite`. Use `--global` to ignore the local `vite-plus` package. Use
`vp why <package>` to show the package-manager dependency graph.

## Review Checklist

- [ ] Run `vp install` after pulling remote changes and before getting started.
- [ ] Run `vp check` and `vp test` to format, lint, type check and test changes.
- [ ] Check if there are `vite.config.ts` tasks or `package.json` scripts necessary for validation, run via `vp run <script>`.
- [ ] If setup, runtime, or package-manager behavior looks wrong, run `vp env doctor` and include its output when asking for help.

<!--VITE PLUS END-->

## SDD + TDD 工作流

本项目使用 OpenSpec 管理规格驱动开发（SDD），使用 Superpowers 执行测试驱动开发（TDD），使用 yuki-agent-kit 维护项目事实、Notes 和质量护栏。

### 标准流程

1. 需求不清或存在方案分歧时，先使用 `openspec-explore` 梳理目标、约束和备选方案。
2. 使用 `openspec-propose` 创建变更，并完成 proposal、spec、design 和 tasks。
3. 使用 `openspec-apply` 按任务实施；每个行为变更遵循 TDD 的 Red → Green → Refactor。
4. 实施后运行 `pnpm exec vp check` 和 `pnpm run build`；涉及测试时运行项目实际存在的测试命令。
5. 使用 `code-review` 检查正确性与回归风险，使用 `find-simplifications` 查找有证据支持的简化机会。
6. 验证通过后使用 `openspec-archive` 归档变更；长期有效的工程决策记录到 `.agents/notes/implemented/`。

### 协作边界

- OpenSpec 负责做什么、为什么做、范围和完成条件。
- Superpowers 负责如何安全实现：TDD、计划执行、审查和完成前验证。
- yuki-agent-kit 负责项目事实、产品上下文、决策记录和 Git 规则。
- 不重复编写同一份计划；OpenSpec tasks 是变更计划的唯一事实来源。
- 不执行不可逆操作、外部写入、部署或权限升级，除非用户明确确认。

### 当前项目验证命令

```bash
pnpm exec vp check
pnpm run build
```

当前 `package.json` 没有独立的测试脚本；新增测试框架或测试脚本时，必须同步更新本节。
