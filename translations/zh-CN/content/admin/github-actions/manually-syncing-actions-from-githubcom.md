---
title: 手动从 GitHub.com 同步操作
intro: '对于需要访问 {% data variables.product.prodname_dotcom_the_website %} 上操作的用户，您可以将特定操作同步到企业。'
redirect_from:
  - /enterprise/admin/github-actions/manually-syncing-actions-from-githubcom
versions:
  enterprise-server: '>=2.22'
  github-ae: next
topics:
  - Enterprise
---

{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}
{% data reusables.actions.ae-beta %}

{% data reusables.actions.enterprise-no-internet-actions %}

推荐的允许从 {% data variables.product.prodname_dotcom_the_website %} 访问操作的方法是启用自动访问所有操作。 通过使用 {% data variables.product.prodname_github_connect %} 将 {% data variables.product.product_name %} 与 {% data variables.product.prodname_ghe_cloud %} 集成可实现这一点。 更多信息请参阅“[启用使用 {% data variables.product.prodname_github_connect %} 自动访问 {% data variables.product.prodname_dotcom_the_website %} 操作](/enterprise/admin/github-actions/enabling-automatic-access-to-githubcom-actions-using-github-connect)”。

但是，如果您想更严格地控制企业中允许的操作，您可以按照本指南使用 {% data variables.product.company_short %} 的开源 [`actions-sync`](https://github.com/actions/actions-sync) 工具将各个操作仓库从 {% data variables.product.prodname_dotcom_the_website %} 同步到企业。

### 关于 `actions-sync` 工具

`actions-sync` 工具必须在可以访问 {% data variables.product.prodname_dotcom_the_website %} API 和 {% data variables.product.product_name %} 实例的 API 的计算机上运行。 计算机不需要同时连接到两者。

如果计算机可以同时访问这两个系统，您可以使用单一 `actions-sync sync` 命令进行同步。 如果您一次只能访问一个系统，您可以使用 `actions-sync pull` 和 `push` 命令。

`actions-sync` 工具只能从存储在公有仓库中的 {% data variables.product.prodname_dotcom_the_website %} 下载操作。

### 基本要求

* 在使用 `actions-sync` 工具之前，您必须确保所有目标组织已经存在于您的企业中。 以下示例演示如何将操作同步到名为 `synced-actions` 的组织。 更多信息请参阅“[从头开始创建新组织](/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch)”。
* 您必须在企业上创建可以创建并写入目标组织中的仓库的个人访问令牌 (PAT)。 更多信息请参阅“[创建个人访问令牌](/github/authenticating-to-github/creating-a-personal-access-token)”。
* 如果您想同步 {% data variables.product.product_location %} 上 `actions` 组织中的捆绑操作，您必须是 `actions` 组织的所有者。

  {% note %}

  **注意：** 默认情况下，即使站点管理员也不是捆绑的 `actions` 组织的所有者。

  {% endnote %}

  站点管理员可以在管理 shell 中使用 `ghe-org-admin-promot-promotion` 命令将用户升级为捆绑的 `actions` 组织的所有者。 更多信息请参阅“[访问管理 shell (SSH)](/admin/configuration/accessing-the-administrative-shell-ssh)”和“[`ghe-org-admin-promote`](/admin/configuration/command-line-utilities#ghe-org-admin-promote)”。

  ```shell
  ghe-org-admin-promote -u <em>USERNAME</em> -o actions
  ```

### 示例：使用 `actions-sync` 工具

此示例演示使用 `actions-sync` 工具将个别操作从 {% data variables.product.prodname_dotcom_the_website %} 同步到企业实例。

{% note %}

**注：**此示例使用 `actions-sync sync` 命令 它要求从您的计算机同时访问 {% data variables.product.prodname_dotcom_the_website %} API 和企业实例的 API。 如果您一次只能访问一个系统，您可以使用 `actions-sync pull` 和 `push` 命令。 更多信息请参阅 [`actions-sync` README](https://github.com/actions/actions-sync#not-connected-instances)。

{% endnote %}

1. 为您计算机的操作系统下载并解压缩最新的 [`actions-sync` 版本](https://github.com/actions/actions-sync/releases)。
1. 创建一个目录来存储工具的缓存文件。
1. 运行 `actions-sync sync` 命令：

   ```shell
   ./actions-sync sync \
     --cache-dir "cache" \
     --destination-token "aabbccddeeffgg" \
     --destination-url "https://my-ghes-instance" \
     --repo-name "docker/build-push-action:synced-actions/docker-build-push-action"
   ```

   上述命令使用以下参数：

   * `--cache-dir`：运行命令的计算机上的缓存目录。
   * `--destination-toke`：目标企业实例的个人访问令牌。
   * `--destination-url`：目标企业实例的 URL。
   * `--repo-name`：要同步的操作仓库。 这将使用格式 `owner/repository:destination_owner/destination_repository`。

     * 上面的示例将 [`docker/build-push-action`](https://github.com/docker/build-push-action) 仓库同步到目标企业实例上的 `synced-actions/docker-build-push-action` 仓库。 在运行上述命令之前，您必须在企业中创建名为 `synced-actions` 的组织。
     * 如果您省略 `:destination_owners/destination_repost`，工具将使用企业的原始所有者和仓库名称。 在运行命令之前，必须在企业中创建一个与操作的所有者名称匹配的新组织。 考虑使用一个中心组织来存储企业中同步的操作，因为这样在同步来自不同所有者的操作时，将无需创建多个新的组织。
     * 将 `--repo-name` 参数替换为 `--repo-name-list` 或 `--repo-name-list-file` 便可同步多个操作。 更多信息请参阅 [`actions-sync` README](https://github.com/actions/actions-sync#actions-sync)。
1. 在企业中创建操作仓库后，企业中的人员可以使用目标仓库在其工作流程中引用操作。 对于上面显示的示例操作：

   ```yaml
   uses: synced-actions/docker-build-push-action@v1
   ```

   更多信息请参阅“[GitHub Actions 的工作流程语法](/actions/reference/workflow-syntax-for-github-actions#jobsjob_idstepsuses)”。
