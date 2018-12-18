---
title: ClickOnce – Manifest nasazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 96ce7d873c20b8c29e5586a54c577a5d744b0caa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306784"
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce – manifest nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manifest nasazení je soubor XML, který popisuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, včetně identifikace aktuální [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verze aplikace pro nasazení.  
  
 Manifesty nasazení mají následující prvky a atributy.  
  
|Prvek|Popis|Atributy|  
|-------------|-----------------|----------------|  
|[\<sestavení > – Element](../deployment/assembly-element-clickonce-deployment.md)|Požadováno. Element nejvyšší úrovně.|`manifestVersion`|  
|[\<Vlastnost assemblyIdentity > – Element](../deployment/assemblyidentity-element-clickonce-deployment.md)|Požadováno. Identifikuje manifest aplikace pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<Popis > – Element](../deployment/description-element-clickonce-deployment.md)|Požadováno. Určuje informace o aplikaci použít k vytvoření prostředí prezentace a **přidat nebo odebrat programy** v Ovládacích panelech.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<nasazení > – Element](../deployment/deployment-element-clickonce-deployment.md)|Volitelné. Určuje atributy použité pro nasazení aktualizací a vystavení systému.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks > – Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)|Požadováno. Určuje verzi rozhraní .NET Framework, ve kterém můžete tuto aplikaci nainstalovat a spustit.|`SupportUrl`|  
|[\<závislost > – Element](../deployment/dependency-element-clickonce-deployment.md)|Požadováno. Určuje verzi aplikace k instalaci pro nasazení a umístění manifestu aplikace.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity – > – Element](../deployment/publisheridentity-element-clickonce-deployment.md)|Vyžaduje se pro podepsané manifesty. Obsahuje informace o vydavateli, který podepsal manifestu nasazení.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<Podpis > – Element](../deployment/signature-element-clickonce-deployment.md)|Volitelné. Obsahuje informace potřebné k digitálnímu podpisu manifestu nasazení.|Žádné|  
|[\<customErrorReporting > – Element](../deployment/customerrorreporting-element-clickonce-deployment.md)|Volitelné. Určuje identifikátor URI, chcete-li zobrazit, když dojde k chybě.|Identifikátor URI|  
  
## <a name="remarks"></a>Poznámky  
 Identifikuje soubor manifestu nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace, včetně aktuální verze a další nastavení nasazení. Odkazuje na manifest aplikace, která popisuje aktuální verzi aplikace a všechny soubory obsažené v nasazení.  
  
 Další informace najdete v tématu [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Umístění souboru  
 Soubor manifestu nasazení odkazuje na správný manifest aplikace pro aktuální verzi aplikace. Když vytvoříte novou verzi nasazení aplikace k dispozici, je nutné aktualizovat manifest nasazení pro odkazování na nový manifest aplikace.  
  
 Soubor manifestu nasazení musí mít silný název a může také obsahovat certifikáty pro ověření vydavatele.  
  
## <a name="file-name-syntax"></a>Syntaxe názvu souboru  
 Název souboru manifestu nasazení musí končit příponou .application.  
  
## <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje manifestu nasazení.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)



