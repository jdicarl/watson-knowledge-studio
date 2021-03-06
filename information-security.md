---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-27"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

If you need to request GDPR support for {{site.data.keyword.cloud}} {{site.data.keyword.watson}} resources that are created

- In the European Union, see [Requesting support for IBM Cloud Watson resources created in the European Union ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/watson/getting-started-gdpr-sar.html#request-EU){: new_window}.
- Outside the European Union, see [Requesting support for resources outside the European Union ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU){: new_window}.

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/gdpr){: new_window}.

## GDPR in {{site.data.keyword.knowledgestudioshort}}
{: #gdpr-wks}

{{site.data.keyword.knowledgestudiofull}} provides a graphical interface through which you can access and delete uploaded artifacts that contain data. The following artifacts can be uploaded to {{site.data.keyword.knowledgestudioshort}}:
- Type systems
- Dictionaries
- Documents

If you receive a request to delete data, complete the following steps:
1. [Delete the applicable artifact](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-artifacts).
2. [Retrain and redeploy the model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-train-ml).
3. [Delete previous versions of the model that used the deleted data](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-improve-ml#wks_maversions).
