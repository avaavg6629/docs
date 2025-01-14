---
title: GitHub Connect を使用して GitHub.com アクションへの自動アクセスを有効にする
intro: 'To allow {% data variables.product.prodname_actions %} in your enterprise to use actions from {% data variables.product.prodname_dotcom_the_website %}, you can connect your enterprise instance to {% data variables.product.prodname_ghe_cloud %}.'
permissions: 'Site administrators for {% data variables.product.product_name %} who are also owners of the connected {% data variables.product.prodname_ghe_cloud %} organization or enterprise account can enable access to all {% data variables.product.prodname_dotcom_the_website %} actions.'
redirect_from:
  - /enterprise/admin/github-actions/enabling-automatic-access-to-githubcom-actions-using-github-connect
versions:
  enterprise-server: '>=2.22'
  github-ae: next
type: how_to
topics:
  - Actions
  - Enterprise
  - GitHub Connect
---

{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}
{% data reusables.actions.enterprise-github-connect-warning %}
{% data reusables.actions.ae-beta %}

デフォルトでは、{% data variables.product.product_name %} の {% data variables.product.prodname_actions %} ワークフローは {% data variables.product.prodname_dotcom_the_website %} または [{% data variables.product.prodname_marketplace %}](https://github.com/marketplace?type=actions) から直接アクションを使用できません。

{% data variables.product.prodname_dotcom_the_website %} のすべてのアクションを Enterprise インスタンスで使用できるようにするには、{% data variables.product.prodname_github_connect %} を使用して {% data variables.product.product_name %} を {% data variables.product.prodname_ghe_cloud %} と統合します。 For other ways of accessing actions from {% data variables.product.prodname_dotcom_the_website %}, see "[About using actions in your enterprise](/admin/github-actions/about-using-actions-in-your-enterprise)."

### すべての {% data variables.product.prodname_dotcom_the_website %} アクションへの自動アクセスを有効化する

Before enabling access to all actions from {% data variables.product.prodname_dotcom_the_website %} on your enterprise instance, you must connect your enterprise to {% data variables.product.prodname_dotcom_the_website %}. 詳細は、「[{% data variables.product.prodname_ghe_server %}を{% data variables.product.prodname_ghe_cloud %}に接続する](/enterprise/{{ currentVersion }}/admin/guides/installation/connecting-github-enterprise-server-to-github-enterprise-cloud)」を参照してください。

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.github-connect-tab %}
1. [Server can use actions from GitHub.com in workflows runs] で、ドロップダウンメニューを使用して [**Enabled**] を選択します。 ![ワークフロー実行内の GitHub.com からアクションへのドロップダウンメニュー](/assets/images/enterprise/site-admin-settings/enable-marketplace-actions-drop-down.png)
1. {% data reusables.actions.enterprise-limit-actions-use %}
