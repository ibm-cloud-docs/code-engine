---

copyright:
  years: 2021
lastupdated: "2021-07-02"

keywords: troubleshooting for code engine subscriptions, subscriptions, tips for subscriptions, ping, object storage

subcollection: codeengine

content-type: troubleshoot

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Why is my `subscription cos create` command failing?
{: #ts-cossub-create}
{: troubleshoot}

{: tsSymptoms}
You cannot create an {{site.data.keyword.cos_full_notm}} subscription through the CLI by using the 
[**`ibmcloud ce subscription cos create`**](/docs/codeengine?topic=codeengine-cli#cli-subscription-cos-create) command and you receive an error that mentions `failed` in the message.

{: tsCauses}
If you cannot create an {{site.data.keyword.cos_short}} subscription, determine whether one of the following cases is true,

1. The name of your subscription is not unique within the project. 

2. The application reference doesn't exist. An error with the following message appears, `Failed to retrieve the application. View available applications by running ibmcloud ce app list`.

3. A timeout occurs. Error message mentions `Getting COS event subscription status timed out`

{: tsResolve}
Try one of these solutions,

1. Run the [`ibmcloud ce sub cos list`](/docs/codeengine?topic=codeengine-cli#cli-subscription-cos-list) command to list all defined {{site.data.keyword.cos_short}} subscriptions and check whether a subscription with the same name exists. If a subscription with the same name exists, run the [`ibmcloud ce sub cos delete --name SUB_NAME`](/docs/codeengine?topic=codeengine-cli#cli-subscription-cos-delete) to delete the old subscription. The name of the subscription must be unique within your project.

2. Run the [**`ibmcloud ce app list`**](/docs/codeengine?topic=codeengine-cli#cli-application-list) command to make sure that your destination app exists. If the app doesn't exist, create the application with the [**`ibmcloud ce app create`**](/docs/codeengine?topic=codeengine-cli#cli-application-create) command.

3. Try the solutions in [Why does my {{site.data.keyword.cos_short}} subscription never become ready?](/docs/codeengine?topic=codeengine-ts-cossub-notready).

