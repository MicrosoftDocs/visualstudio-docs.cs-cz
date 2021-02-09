---
title: '&lt;Dependency – &gt; element (aplikace ClickOnce) | Microsoft Docs'
description: Element Dependency identifikuje závislost platformy nebo sestavení, která je vyžadována pro aplikaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e716c0e9ebe88a8007296f1dad870424a0def0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881110"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Dependency – &gt; element (aplikace ClickOnce)
Identifikuje závislost platformy nebo sestavení, která je pro aplikaci nutná.

## <a name="syntax"></a>Syntax

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `dependency`Element je povinný. `dependency`Ve stejném manifestu aplikace může být více instancí.

 `dependency`Element nemá žádné atributy a obsahuje následující podřízené prvky.

### <a name="dependentos"></a>dependentOS
 Nepovinný parametr. Obsahuje `osVersionInfo` element. `dependentOS`Elementy a `dependentAssembly` se vzájemně vylučují: jeden nebo druhý musí existovat pro `dependency` prvek, ale ne obojí.

 `dependentOS` podporuje následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`supportUrl`|Nepovinný parametr. Určuje adresu URL podpory pro závislých platforem. Tato adresa URL se zobrazí uživateli, pokud je nalezena požadovaná platforma.|
|`description`|Nepovinný parametr. Popisuje, jak je uživatelsky čitelné formuláře, operační systém, který je popsán v `dependentOS` prvku.|

### <a name="osversioninfo"></a>osVersionInfo
 Povinná hodnota. Tento prvek je podřízeným prvkem `dependentOS` prvku a obsahuje `os` prvek. Tento element nemá žádné atributy.

### <a name="os"></a>os
 Povinná hodnota. Tento prvek je podřízeným `osVersionInfo` prvkem elementu. Tento element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`majorVersion`|Povinná hodnota. Určuje hlavní číslo verze operačního systému.|
|`minorVersion`|Povinná hodnota. Určuje číslo dílčí verze operačního systému.|
|`buildNumber`|Povinná hodnota. Určuje číslo sestavení operačního systému.|
|`servicePackMajor`|Povinná hodnota. Určuje hlavní číslo aktualizace Service Pack operačního systému.|
|`servicePackMinor`|Nepovinný parametr. Určuje menší číslo aktualizace Service Pack operačního systému.|
|`productType`|Nepovinný parametr. Identifikuje hodnotu typu produktu. Platné hodnoty jsou `server` , `workstation` a `domainController` . Například pro systém Windows 2000 Professional je tato hodnota atributu `workstation` .|
|`suiteType`|Nepovinný parametr. Identifikuje produktovou sadu, která je k dispozici v systému, nebo typ konfigurace systému. Platné hodnoty jsou `backoffice` , `blade` , `datacenter` , `enterprise` , `home` , `professional` , `smallbusiness` , `smallbusinessRestricted` a `terminal` . Například pro systém Windows 2000 Professional je tato hodnota atributu `professional` .|

### <a name="dependentassembly"></a>dependentAssembly
 Nepovinný parametr. Obsahuje `assemblyIdentity` element. `dependentOS`Elementy a `dependentAssembly` se vzájemně vylučují: jeden nebo druhý musí existovat pro `dependency` prvek, ale ne obojí.

 `dependentAssembly` má následující atributy.

| Atribut | Popis |
|-----------------------| - |
| `dependencyType` | Povinná hodnota. Určuje typ závislosti. Platné hodnoty jsou `preprequisite` a `install` . `install`Sestavení je nainstalováno jako součást [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. Aby bylo `prerequisite` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] možné aplikaci nainstalovat, musí být sestavení přítomna v globální mezipaměti sestavení (GAC). |
| `allowDelayedBinding` | Povinná hodnota. Určuje, zda lze sestavení načíst programově v době běhu. |
| `group` | Nepovinný parametr. Pokud `dependencyType` je atribut nastaven na `install` , označuje pojmenovanou skupinu sestavení, která se instalují pouze na vyžádání. Další informace naleznete v tématu [Návod: stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Pokud je nastavena na `framework` a `dependencyType` atribut je nastaven na `prerequisite` , označuje sestavení jako součást .NET Framework. Globální mezipaměť Assemby (GAC) není pro toto sestavení kontrolována při instalaci na .NET Framework 4 a novějších verzích. |
| `codeBase` | Vyžaduje se, když `dependencyType` je atribut nastavený na `install` . Cesta k závislému sestavení Může se jednat o absolutní cestu nebo o cestu relativní vzhledem k základu kódu manifestu. Aby byl manifest sestavení platný, musí být tato cesta platným identifikátorem URI. |
| `size` | Vyžaduje se, když `dependencyType` je atribut nastavený na `install` . Velikost závislého sestavení (v bajtech). |

### <a name="assemblyidentity"></a>assemblyIdentity
 Povinná hodnota. Tento prvek je podřízeným `dependentAssembly` prvkem prvku a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Povinná hodnota. Určuje název aplikace.|
|`version`|Povinná hodnota. Určuje číslo verze aplikace v následujícím formátu: `major.minor.build.revision`|
|`publicKeyToken`|Nepovinný parametr. Určuje 16 znaků šestnáctkový řetězec, který představuje posledních 8 bajtů `SHA-1` hodnoty hash veřejného klíče, pod nímž je aplikace nebo sestavení podepsáno. Veřejný klíč, který se používá k podepsání katalogu, musí mít 2048 nebo více bitů.|
|`processorArchitecture`|Nepovinný parametr. Určuje procesor. Platné hodnoty jsou `x86` pro 32 – 32bitová okna a `I64` pro 64-bitové okna.|
|`language`|Nepovinný parametr. Určuje dva kódy jazyků, například EN-US, sestavení.|

### <a name="hash"></a>hash
 `hash`Element je volitelný podřízený `assemblyIdentity` prvek elementu. `hash`Element nemá žádné atributy.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] používá algoritmus hash pro všechny soubory v aplikaci jako kontrolu zabezpečení, aby se zajistilo, že žádný ze souborů nebyl po nasazení změněn. Není `hash` -li prvek zahrnut, tato kontrolu nebude provedena. Proto vynechání `hash` elementu není doporučeno.

### <a name="dsigtransforms"></a>dsig: transformes
 `dsig:Transforms`Element je požadovaný podřízený `hash` prvek elementu. `dsig:Transforms`Element nemá žádné atributy.

### <a name="dsigtransform"></a>dsig: transformace
 `dsig:Transform`Element je požadovaný podřízený `dsig:Transforms` prvek elementu. `dsig:Transform`Element má následující atributy.

| Atribut | Popis |
|-------------| - |
| `Algorithm` | Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou používá, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je `urn:schemas-microsoft-com:HashTransforms.Identity` . |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestMethod`Element má následující atributy.

| Atribut | Popis |
|-------------| - |
| `Algorithm` | Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou používá, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je `http://www.w3.org/2000/09/xmldsig#sha1` . |

### <a name="dsigdigestvalue"></a>dsig: DigestValue
 `dsig:DigestValue`Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestValue`Element nemá žádné atributy. Jeho textová hodnota je vypočtená hodnota hash pro zadaný soubor.

## <a name="remarks"></a>Poznámky
 Všechna sestavení, která vaše aplikace používá, musí mít odpovídající `dependency` element. Závislá sestavení neobsahují sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC) jako sestavení platformy.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `dependency` elementy v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikace. Tento příklad kódu je součástí většího příkladu, který je k dispozici v tématu [manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Viz také
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<dependency> objekt](../deployment/dependency-element-clickonce-deployment.md)