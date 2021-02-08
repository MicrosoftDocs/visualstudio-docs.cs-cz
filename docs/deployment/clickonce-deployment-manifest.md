---
title: Manifest nasazení ClickOnce | Microsoft Docs
description: Seznamte se s manifestem nasazení, souborem XML, který popisuje nasazení ClickOnce, včetně aktuální verze aplikace ClickOnce k nasazení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3e8737a29fed109e82240a74569011be60a586c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840857"
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce – manifest nasazení
Manifest nasazení je soubor XML, který popisuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, včetně identifikace aktuální [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verze aplikace, která má být nasazena.

 Manifesty nasazení mají následující elementy a atributy.

| Element | Popis | Atributy |
| - | - | - |
| [\<assembly> Objekt](../deployment/assembly-element-clickonce-deployment.md) | Povinná hodnota. Element nejvyšší úrovně. | `manifestVersion` |
| [\<assemblyIdentity> Objekt](../deployment/assemblyidentity-element-clickonce-deployment.md) | Povinná hodnota. Identifikuje manifest aplikace pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture` |
| [\<description> Objekt](../deployment/description-element-clickonce-deployment.md) | Povinná hodnota. Identifikuje informace o aplikaci používané k vytvoření stavu prostředí a položky **Přidat nebo odebrat programy** v Ovládacích panelech. | `publisher`<br /><br /> `product`<br /><br /> `supportUrl` |
| [\<deployment> Objekt](../deployment/deployment-element-clickonce-deployment.md) | Nepovinný parametr. Určuje atributy používané pro nasazení aktualizací a expozici systému. | `install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters` |
| [\<compatibleFrameworks> Objekt](../deployment/compatibleframeworks-element-clickonce-deployment.md) | Povinná hodnota. Identifikuje verze .NET Framework, kde se tato aplikace může nainstalovat a spustit. | `SupportUrl` |
| [\<dependency> Objekt](../deployment/dependency-element-clickonce-deployment.md) | Povinná hodnota. Určuje verzi aplikace, která se má nainstalovat pro nasazení, a umístění manifestu aplikace. | `preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size` |
| [\<publisherIdentity> Objekt](../deployment/publisheridentity-element-clickonce-deployment.md) | Vyžaduje se pro podepsané manifesty. Obsahuje informace o vydavateli, který podepsal tento manifest nasazení. | `Name`<br /><br /> `issuerKeyHash` |
| [\<Signature> Objekt](../deployment/signature-element-clickonce-deployment.md) | Nepovinný parametr. Obsahuje nezbytné informace pro Digitální podepsání tohoto manifestu nasazení. | Žádné |
| [\<customErrorReporting> Objekt](../deployment/customerrorreporting-element-clickonce-deployment.md) | Nepovinný parametr. Určuje identifikátor URI, který se má zobrazit, když dojde k chybě. | Identifikátor URI |

## <a name="remarks"></a>Poznámky
 Soubor manifestu nasazení identifikuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace, včetně aktuální verze a dalších nastavení nasazení. Odkazuje na manifest aplikace, který popisuje aktuální verzi aplikace a všechny soubory obsažené v nasazení.

 Další informace najdete v tématu [zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Umístění souboru
 Soubor manifestu nasazení odkazuje na správný manifest aplikace pro aktuální verzi aplikace. Pokud zpřístupníte novou verzi nasazení aplikace, je nutné aktualizovat manifest nasazení, aby odkazoval na nový manifest aplikace.

 Soubor manifestu nasazení musí mít silný název a může také obsahovat certifikáty pro ověření vydavatele.

## <a name="file-name-syntax"></a>Syntaxe názvu souboru
 Název souboru manifestu nasazení musí končit příponou *. Application* .

## <a name="examples"></a>Příklady
 Následující příklad kódu ukazuje manifest nasazení.

```xml
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
...
</Signature></asmv1:assembly>
```

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)