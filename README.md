# CWTools config rules for Stellaris
.cwt config files for Stellaris

These will be used automatically, using the latest tag for `stable` and the latest commit for `latest`.
To manually use for testing or contributing, copy the contents of the config folder and place it in a folder called `.cwtools` in the folder you open in vscode.

See https://github.com/tboby/cwtools/wiki/.cwt-config-file-guidance for guidance on the file format

### Contributing
If you'd like to contribute, press the pen icon on any file, then press "Create a new branch for this commit and start a pull request". You can then make further changes as a "pull request". When done, mention it in the pull request and your changes will be included.

## Integration with cwtools-vscode

This repository is included by
[`cwtools-vscode`](https://github.com/Aa728848/cwtools-vscode) as the
`submodules/cwtools-stellaris-config` Git submodule. Its `config/` directory is
the development baseline for Stellaris CWT rules, rules-sync reports, and the
fallback rules archive bundled into the extension at
`release/rules/stellaris-rules.zip`.

### Change boundary

- Treat changes here as rules-data updates, not extension runtime changes.
- Put `.cwt` rules and closely related configuration content under `config/`.
- Keep parser or validation-engine semantics in the sibling
  `submodules/cwtools` repository.
- Keep rule synchronization code, packaging, UI, and extension behavior in the
  parent `cwtools-vscode` repository.
- Follow `.editorconfig`; `.cwt` files use tabs and trimmed trailing whitespace.

### Development and verification

From the parent repository root, use the rules workflow to compare this
baseline with Stellaris `script_documentation` and vanilla `common/`, then run
the rules contracts:

```bash
npm run rules:stellaris:check
npm run rules:stellaris:contracts
```

Use `npm run rules:stellaris:report` when a human-readable drift report is
needed. See the parent's
[`docs/cwt-rule-config.md`](https://github.com/Aa728848/cwtools-vscode/blob/main/docs/cwt-rule-config.md)
for authoring details.
Packaging also requires this submodule to be initialized because its `config/`
directory is compressed into the fallback rules bundle.

Commit rules changes inside this submodule first, then return to the parent
repository and commit the updated submodule pointer separately. Explain the
rules baseline change in the parent pull request.

## 与 cwtools-vscode 的集成

本仓库作为 `submodules/cwtools-stellaris-config` Git 子模块集成到
[`cwtools-vscode`](https://github.com/Aa728848/cwtools-vscode) 中。它的
`config/` 目录是 Stellaris CWT 规则、规则同步报告和扩展 fallback 规则包的开发
基线；打包时会生成 `release/rules/stellaris-rules.zip`。

### 修改边界

- 本仓库的修改属于规则数据更新，不属于扩展运行时代码修改。
- `.cwt` 规则及紧密相关的配置内容应放在 `config/` 下。
- 解析器或校验引擎语义应放在相邻的 `submodules/cwtools` 仓库。
- 规则同步代码、打包逻辑、UI 和扩展行为应留在父仓库 `cwtools-vscode`。
- 遵循 `.editorconfig`；`.cwt` 文件使用 Tab 缩进并移除行尾空白。

### 开发与验证

在父仓库根目录使用规则工作流，将当前基线与 Stellaris
`script_documentation` 和原版 `common/` 对比，然后运行规则合约测试：

```bash
npm run rules:stellaris:check
npm run rules:stellaris:contracts
```

需要便于人工阅读的差异报告时，运行 `npm run rules:stellaris:report`。规则编写细节
见父仓库的
[`docs/cwt-rule-config.md`](https://github.com/Aa728848/cwtools-vscode/blob/main/docs/cwt-rule-config.md)。
打包同样要求初始化本子模块，因为 `config/` 会被压缩为 fallback 规则包。

请先在本子模块内部提交规则修改，再回到父仓库单独提交更新后的 submodule 指针，
并在父仓库的 Pull Request 中说明规则基线发生了什么变化。
