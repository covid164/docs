---
title: Habilitar alertas para dependências vulneráveis no GitHub Enterprise Server
intro: 'Você pode conectar {% data variables.product.product_location_enterprise %} a {% data variables.product.prodname_ghe_cloud %} e habilitar {% if currentVersion ver_gt "enterprise-server@2. 1" %}{% data variables.product.prodname_dependabot_short %}{% else %}alertas de segurança{% endif %} para dependências vulneráveis nos repositórios na sua instância.'
redirect_from:
  - /enterprise/admin/installation/enabling-security-alerts-for-vulnerable-dependencies-on-github-enterprise-server
  - /enterprise/admin/configuration/enabling-security-alerts-for-vulnerable-dependencies-on-github-enterprise-server
  - /enterprise/admin/configuration/enabling-alerts-for-vulnerable-dependencies-on-github-enterprise-server
permissions: 'Os administradores do site de {% data variables.product.prodname_ghe_server %} que também são proprietários da organização ou conta corporativa conectada {% data variables.product.prodname_ghe_cloud %} podem habilitar {% if currentVersion ver_gt "enterprise-server@2. 1" %}{% data variables.product.prodname_dependabot_short %}{% else %}alertas de segurança{% endif %} para dependências vulneráveis em {% data variables.product.prodname_ghe_server %}.'
versions:
  enterprise-server: '*'
---

### Sobre alertas para dependências vulneráveis no {% data variables.product.prodname_ghe_server %}

{% data reusables.repositories.tracks-vulnerabilities %} Para obter mais informações, consulte "[Sobre alertas de dependências vulneráveis](/github/managing-security-vulnerabilities/about-alerts-for-vulnerable-dependencies)".

Você pode conectar {% data variables.product.product_location_enterprise %} a {% data variables.product.prodname_dotcom_the_website %} e, em seguida, sincronizar os dados de vulnerabilidade na instância e gerar {% if currentVersion ver_gt "enterprise-server@2. 1" %}{% data variables.product.prodname_dependabot_short %}{% else %}alertas de segurança{% endif %} em repositórios com uma dependência vulnerável.

Depois de conectar {% data variables.product.product_location_enterprise %} a {% data variables.product.prodname_dotcom_the_website %} e habilitar {% if currentVersion ver_gt "enterprise-server@2. 1" %}{% data variables.product.prodname_dependabot_short %}{% else %}alertas de segurança{% endif %} para dependências vulneráveis, os dados de vulnerabilidade serão sincronizados de {% data variables.product.prodname_dotcom_the_website %} para a sua instância uma vez por hora. Também é possível sincronizar os dados de vulnerabilidade manualmente a qualquer momento. Nenhum código ou informações sobre o código da {% data variables.product.product_location_enterprise %} são carregados para o {% data variables.product.prodname_dotcom_the_website %}.

{% if currentVersion ver_gt "enterprise-server@2. 1" %}Quando {% data variables.product.product_location_enterprise %} recebe informações sobre uma vulnerabilidade, ele identificará repositórios na sua instância que usam a versão afetada da dependência e enviará alertas de {% data variables.product.prodname_dependabot_short %} para proprietários e pessoas com acesso de administrador nesses repositórios. Eles podem personalizar a forma como recebem os alertas de {% data variables.product.prodname_dependabot_short %}. Para obter mais informações, consulte "[Sobre alertas para dependências vulneráveis](/github/managing-security-vulnerabilities/about-alerts-for-vulnerable-dependencies/#configuring-notifications-for-github-dependabot-alerts)"
{% endif %}

{% if currentVersion ver_lt "enterprise-server@2.21" or currentVersion == "enterprise-server@2. 1" %}Quando {% data variables.product.product_location_enterprise %} recebe informações sobre uma vulnerabilidade, ele identificará repositórios na sua instância que usam a versão afetada da dependência e enviará alertas de segurança a proprietários e pessoas com acesso de administrador nesses repositórios. É possível personalizar o recebimento dos alertas de segurança. Para obter mais informações, consulte "[Sobre alertas para dependências vulneráveis](/github/managing-security-vulnerabilities/about-alerts-for-vulnerable-dependencies/#configuring-notifications-for-security-alerts)"
{% endif %}

{% if currentVersion ver_gt "enterprise-server@2.21" %}
### Habilitar alertas de {% data variables.product.prodname_dependabot_short %} para dependências vulneráveis em {% data variables.product.prodname_ghe_server %}
{% else %}
### Habilitar alertas de segurança para dependências vulneráveis no {% data variables.product.prodname_ghe_server %}
{% endif %}

Antes de habilitar {% if currentVersion ver_gt "enterprise-server@2. 1" %}{% data variables.product.prodname_dependabot_short %}{% else %}alertas de segurança{% endif %} de dependências vulneráveis em {% data variables.product.product_location_enterprise %}, você deve conectar {% data variables.product.product_location_enterprise %} a {% data variables.product.prodname_dotcom_the_website %}. Para obter mais informações, consulte "[Conectar o {% data variables.product.prodname_ghe_server %} ao {% data variables.product.prodname_ghe_cloud %}](/enterprise/{{ currentVersion }}/admin/guides/installation/connecting-github-enterprise-server-to-github-enterprise-cloud)".

{% if currentVersion ver_gt "enterprise-server@2.20" %}

{% if currentVersion ver_gt "enterprise-server@2.21" %}Recomendamos configurar alertas de {% data variables.product.prodname_dependabot_short %} sem notificações para os primeiros dias a fim de evitar uma sobrecarga de e-mails. Após alguns dias, você poderá habilitar as notificações para receber alertas de {% data variables.product.prodname_dependabot_short %}, como de costume.{% endif %}

{% if currentVersion == "enterprise-server@2.21" %}Recomendamos configurar alertas de segurança sem notificações nos primeiros dias para evitar uma sobrecarga de e-mails. Após alguns dias, você pode habilitar notificações para receber alertas de segurança como de costume.{% endif %}

{% endif %}

{% data reusables.enterprise_site_admin_settings.sign-in %}
1. No shell administrativo, habilite os {% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %}alertas de segurança{% endif %} de dependências vulneráveis em {% data variables.product.product_location_enterprise %}:
 ``` shell
$ ghe-dep-graph-enable
```
3. Retornar para
{% data variables.product.prodname_ghe_server %}.
{% data reusables.enterprise_site_admin_settings.access-settings %}
{% data reusables.enterprise_site_admin_settings.business %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.github-connect-tab %}{% if currentVersion ver_gt "enterprise-server@2.20" %}
5. Em "Repositories can be scanned for vulnerabilities" (Os repositórios podem ser examinados para vulnerabilidades), use o menu suspenso e clique em **Enabled without notifications** (Habilitado sem notificações). Opcionalmente, para habilitar alertas com notificações, selecione **Enabled with notifications**(Habilitado com notificações).{% else %}
5. Em "Repositories can be scanned for vulnerabilities" (Verificar vulnerabilidades nos repositórios), use o menu suspenso e clique em **Enabled** (Habilitado).
{% endif %}
   ![Menu suspenso para habilitar a verificação vulnerabilidades nos repositórios](/assets/images/enterprise/site-admin-settings/enable-vulnerability-scanning-in-repositories.png)

### Exibir dependências vulneráveis no {% data variables.product.prodname_ghe_server %}

Você pode exibir todas as vulnerabilidades na {% data variables.product.product_location_enterprise %} e sincronizar manualmente os dados de vulnerabilidade do {% data variables.product.prodname_dotcom_the_website %} para atualizar a lista.

{% data reusables.enterprise_site_admin_settings.access-settings %}
2. Na barra lateral esquerda, clique em **Vulnerabilities** (Vulnerabilidades). ![Guia Vulnerabilities (Vulnerabilidades) na barra lateral de administração do site](/assets/images/enterprise/business-accounts/vulnerabilities-tab.png)
3. Para sincronizar os dados de vulnerabilidade, clique em **Sync Vulnerabilities now** (Sincronizar vulnerabilidades agora). ![Botão Sync Vulnerabilities now (Sincronizar vulnerabilidades agora)](/assets/images/enterprise/site-admin-settings/sync-vulnerabilities-button.png)
