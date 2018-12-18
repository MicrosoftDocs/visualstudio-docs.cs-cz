---
title: ClickOnce – Manifest aplikace | Dokumentace Microsoftu
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
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 57e48816ede7210a268cc465da1eee3b6ff43d02
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289585"
---
# <a name="clickonce-application-manifest"></a>ClickOnce – manifest aplikace 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace je soubor XML, který popisuje aplikace, která se nasadí pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty aplikací mají následující prvky a atributy.  
  
|Prvek|Popis|Atributy|  
|-------------|-----------------|----------------|  
|[\<sestavení > – Element](../deployment/assembly-element-clickonce-application.md)|Požadováno. Element nejvyšší úrovně.|`manifestVersion`|  
|[\<Vlastnost assemblyIdentity > – Element](../deployment/assemblyidentity-element-clickonce-application.md)|Požadováno. Určuje primární sestavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo > Element](../deployment/trustinfo-element-clickonce-application.md)|Identifikuje požadavky na zabezpečení aplikace.|Žádné|  
|[\<entryPoint > – Element](../deployment/entrypoint-element-clickonce-application.md)|Požadováno. Určuje vstupní bod pro kód aplikace.|`name`|  
|[\<závislost > – Element](../deployment/dependency-element-clickonce-application.md)|Požadováno. Identifikuje každou závislost vyžaduje pro spuštění aplikace. Volitelně určuje sestavení, které je potřeba provést.|Žádné|  
|[\<Soubor > – Element](../deployment/file-element-clickonce-application.md)|Volitelné. Identifikuje každý nonassembly soubor, který používá aplikace. Izolace dat modelu COM (Component Object) přidružené k souboru může obsahovat.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation > – Element](../deployment/fileassociation-element-clickonce-application.md)|Volitelné. Určuje příponu souboru, který se má přidružit aplikaci.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Soubor manifestu aplikace identifikuje aplikace nasazené pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Další informace o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], naleznete v tématu [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Umístění souboru  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace je specifická pro jednu verzi nasazení. Z tohoto důvodu mají být uloženy odděleně od manifesty nasazení. Běžné konvence je umístit je v podadresáři pojmenovaném přidružené verze.  
  
 Manifest aplikace musí být podepsané vždy před jejich nasazením. Pokud změníte manifest aplikace ručně, musíte použít mage.exe znovu podepsat manifest aplikace, manifest nasazení aktualizovat a znovu podepsat manifest nasazení. Další informace najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="file-name-syntax"></a>Syntaxe názvu souboru  
 Název [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] soubor manifestu aplikace musí být úplný název a příponu aplikace jsme uvedli v `assemblyIdentity` element, za nímž následuje příponu .manifest. Manifest aplikace, který odkazuje na aplikaci Example.exe třeba, použijte následující syntaxe názvu souboru.  
  
 `example.exe.manifest`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje manifest aplikace pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
```  
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
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)



