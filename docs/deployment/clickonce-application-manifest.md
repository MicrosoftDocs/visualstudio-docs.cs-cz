---
title: Manifest aplikace ClickOnce | Microsoft Docs
description: Seznamte se s manifestem aplikace ClickOnce, což je soubor XML, který popisuje aplikaci nasazenou pomocí technologie ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13b84a256bfc9d13f8c17b92385df2106dc0a47d
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383115"
---
# <a name="clickonce-application-manifest"></a>Manifest aplikace ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Manifest aplikace je soubor XML, který popisuje aplikaci, která je nasazena pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty aplikací mají následující elementy a atributy.

| Element | Popis | Atributy |
| - | - | - |
| [\<assembly> Objekt](../deployment/assembly-element-clickonce-application.md) | Povinná hodnota. Element nejvyšší úrovně. | `manifestVersion` |
| [\<assemblyIdentity> Objekt](../deployment/assemblyidentity-element-clickonce-application.md) | Povinná hodnota. Identifikuje primární sestavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> Objekt](../deployment/trustinfo-element-clickonce-application.md) | Určuje požadavky na zabezpečení aplikace. | Žádné |
| [\<entryPoint> Objekt](../deployment/entrypoint-element-clickonce-application.md) | Povinná hodnota. Identifikuje vstupní bod kódu aplikace. | `name` |
| [\<dependency> Objekt](../deployment/dependency-element-clickonce-application.md) | Povinná hodnota. Identifikuje každou závislost nutnou ke spuštění aplikace. Volitelně identifikuje sestavení, která musí být předinstalována. | Žádné |
| [\<file> Objekt](../deployment/file-element-clickonce-application.md) | Nepovinný parametr. Identifikuje všechny nesestaveníelné soubory, které aplikace používá. Může zahrnovat data izolace modelu COM (Component Object Model) přidružená k souboru. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> Objekt](../deployment/fileassociation-element-clickonce-application.md) | Nepovinný parametr. Určuje příponu souboru, která má být přidružena k aplikaci. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Poznámky
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Soubor manifestu aplikace identifikuje aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Další informace o najdete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] v tématu [zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Umístění souboru
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Manifest aplikace je specifický pro jednu verzi nasazení. Z tohoto důvodu by měly být uloženy odděleně od manifestů nasazení. Běžnou konvencí je umístit je do podadresáře s názvem po přidružené verzi.

 Manifest aplikace musí být před nasazením vždy podepsán. Pokud změníte manifest aplikace ručně, je nutné použít *mage.exe* pro opětovné podepsání manifestu aplikace, aktualizaci manifestu nasazení a opětovné podepsání manifestu nasazení. Další informace najdete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="file-name-syntax"></a>Syntaxe názvu souboru
 Název [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] souboru manifestu aplikace by měl být úplný název a přípona aplikace, jak je uvedeno v `assemblyIdentity` elementu a za ním následuje přípona *. manifest*. Například manifest aplikace, který odkazuje na *Example.exe* aplikace, by používal následující syntaxi názvu souboru.

 `example.exe.manifest`

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje manifest aplikace pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)