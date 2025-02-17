---
title: 查看您的 GitHub 高级安全使用情况
intro: 'You can view usage of your {% data variables.product.prodname_GH_advanced_security %} license.'
permissions: 'Enterprise owners can manage access to {% data variables.product.prodname_GH_advanced_security %} for their organization or enterprise organizations.'
product: '{% data reusables.gated-features.ghas %}'
redirect_from: /github/setting-up-and-managing-your-enterprise/managing-use-of-advanced-security-for-organizations-in-your-enterprise-account
versions:
  free-pro-team: '*'
---

{% data reusables.advanced-security.about-ghas-license-seats %} For more information, see "[About licensing for {% data variables.product.prodname_GH_advanced_security %}](/github/setting-up-and-managing-billing-and-payments-on-github/about-licensing-for-github-advanced-security)."

### Viewing {% data variables.product.prodname_GH_advanced_security %} license usage for your enterprise account

You can check how many seats your license includes and how many of them are currently used.

{% data reusables.enterprise-accounts.access-enterprise %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.license-tab %}
   “{% data variables.product.prodname_GH_advanced_security %}”部分显示了当前使用详情。 ![{% data variables.product.prodname_GH_advanced_security %} in enterprise licensing settings](/assets/images/help/enterprises/enterprise-licensing-tab-ghas.png) 如果您的席位用完了，该部分将为红色。 您应该减少您对 {% data variables.product.prodname_GH_advanced_security %} 的使用，或者购买更多席位。 更多信息请参阅“[关于 {% data variables.product.prodname_GH_advanced_security %} 的许可](/github/setting-up-and-managing-billing-and-payments-on-github/about-licensing-for-github-advanced-security#getting-the-most-out-of-your-github-advanced-security-enterprise-license)”。 ![企业许可设置中的 {% data variables.product.prodname_GH_advanced_security %}](/assets/images/help/enterprises/enterprise-licensing-tab-ghas-no-seats.png)
4. （可选）要查看每个组织的使用详情，请在左侧边栏中单击 **Billing（计费）**。 ![Billing tab in the enterprise account settings sidebar](/assets/images/help/business-accounts/settings-billing-tab.png) 在“{% data variables.product.prodname_GH_advanced_security %}”部分，您可以查看每个组织的提交者和唯一提交者数量。 ![企业计费设置中的 {% data variables.product.prodname_GH_advanced_security %}](/assets/images/help/billing/ghas-orgs-list-enterprise-dotcom.png)
5. （可选）单击您是所有者的组织的名称，以显示组织的安全和分析设置。 ![在企业帐单设置的 {% data variables.product.prodname_GH_advanced_security %} 部分中拥有的组织](/assets/images/help/billing/ghas-orgs-list-enterprise-click-org.png)
6. 在“Security & analysis（安全性和分析）”设置页面上，滚动到“{% data variables.product.prodname_GH_advanced_security %} 仓库”部分以查看此组织的仓库使用明细。 ![{% data variables.product.prodname_GH_advanced_security %} repositories section](/assets/images/help/enterprises/settings-security-analysis-ghas-repos-list.png) 更多信息请参阅“[管理组织的安全性和分析设置](/organizations/keeping-your-organization-secure/managing-security-and-analysis-settings-for-your-organization)”。

