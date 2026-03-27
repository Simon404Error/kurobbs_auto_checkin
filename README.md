# Auto Sign Job

你可以在每天指定的时间自动运行签到脚本(包含社区签到和奖励签到)，而无需手动操作。
目前支持库街区

## 如何使用

### 1. Fork 仓库

首先，点击右上角的 `Fork` 按钮，将这个仓库 Fork 到你自己的 GitHub 账户下。

### 2. 设置 GitHub Secrets

为了确保签到脚本能够正常运行，你需要将必要的敏感信息([token](https://blog.tomys.top/2023-07/kuro-token/))存储在 GitHub
Secrets 中。

1. 进入你 Fork 后的仓库页面。
2. 点击 `Settings` 选项卡。
3. 在左侧菜单中选择 `Secrets and variables` > `Actions`。
4. 点击 `New repository secret` 按钮。
5. 在 `Name` 字段中输入 `TOKEN`，在 `Value` 字段中输入你的签到脚本所需的 token。
6. 点击 `Add secret` 保存。

### 3. 修改脚本（可选）

如果你需要修改签到脚本的逻辑，可以编辑 [`auto_checkin.py`](auto_checkin.py) 文件。

### 4. 触发工作流

#### 自动触发

工作流已经配置为每天北京时间早上 6 点（UTC 时间 22:00）自动运行。你无需手动操作，只需确保仓库中的代码和 Secrets 配置正确即可。

#### 手动触发

如果你想立即运行工作流，可以手动触发：

1. 进入你 Fork 后的仓库页面。
2. 点击 `Actions` 选项卡。
3. 在左侧菜单中选择 `Auto Sign Job`。
4. 点击右上角的 `Run workflow` 按钮，选择 `Run workflow` 即可手动触发。

### 5. 查看运行结果

每次工作流运行后，你可以在 `Actions` 选项卡中查看运行结果。如果签到成功，你应该能够看到相应的日志输出。签到失败则会报错。

### 6. 第三方结果推送（可选）

将每日运行结果推送到其他APP当中。

#### Server酱3

1. 前往[Server酱3官网](https://sc3.ft07.com/)，微信扫码登入。
2. SendKey-AppKey管理-添加新的AppKey。
3. 将获得的AppKey写入Github Secrets，`Name`字段为`SERVER3_SEND_KEY`。具体可参考本文的`2. 设置 GitHub Secrets`部分。
4. 下载[APP](https://sc3.ft07.com/client)并登入。

## 注意事项

- 确保 `TOKEN` 的安全性，不要将其直接写在代码中。
- 如果需要修改定时任务的执行时间，可以编辑 [`.github/workflows/auto_sign.yaml`](.github/workflows/auto_checkin.yaml) 文件中的
  `cron` 表达式。
- 如需查看更详细的排查日志，可以在 Secrets 中添加 `DEBUG=true`，日志会自动对 TOKEN、Bark、Server酱等敏感值进行脱敏。

## 特别感谢

本项目的签到脚本部分参考了 [TomyJan-API-Collection](https://github.com/TomyJan/Kuro-API-Collection) 的 API 实现。感谢TomyJan
的开源贡献

## 贡献

如果你有任何改进建议或发现问题，欢迎提交 Issue 或 Pull Request.
