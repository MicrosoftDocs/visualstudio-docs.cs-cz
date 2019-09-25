---
title: '&lt;Dependency&gt; – element (aplikace ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa949aa2f8e718ab0209c54a0ea2160c042a4eb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252485"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Dependency&gt; – element (aplikace ClickOnce)
Identifikuje závislost platformy nebo sestavení, která je pro aplikaci nutná.

## <a name="syntax"></a>Syntaxe

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
 `dependency` Element je povinný. `dependency` Ve stejném manifestu aplikace může být více instancí.

 `dependency` Element nemá žádné atributy a obsahuje následující podřízené prvky.

### <a name="dependentos"></a>dependentOS
 Volitelný parametr. `osVersionInfo` Obsahuje element. Elementy `dependentOS` `dependency` a `dependentAssembly` se vzájemně vylučují: jeden nebo druhý musí existovat pro prvek, ale ne obojí.

 `dependentOS`podporuje následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`supportUrl`|Volitelný parametr. Určuje adresu URL podpory pro závislých platforem. Tato adresa URL se zobrazí uživateli, pokud je nalezena požadovaná platforma.|
|`description`|Volitelný parametr. Popisuje, jak je uživatelsky čitelné formuláře, operační systém, který je `dependentOS` popsán v prvku.|

### <a name="osversioninfo"></a>osVersionInfo
 Povinný parametr. Tento prvek je podřízeným `dependentOS` prvkem prvku a `os` obsahuje prvek. Tento element nemá žádné atributy.

### <a name="os"></a>Jiného
 Povinný parametr. Tento prvek je podřízeným `osVersionInfo` prvkem elementu. Tento element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`majorVersion`|Povinný parametr. Určuje hlavní číslo verze operačního systému.|
|`minorVersion`|Povinný parametr. Určuje číslo dílčí verze operačního systému.|
|`buildNumber`|Povinný parametr. Určuje číslo sestavení operačního systému.|
|`servicePackMajor`|Povinný parametr. Určuje hlavní číslo aktualizace Service Pack operačního systému.|
|`servicePackMinor`|Volitelný parametr. Určuje menší číslo aktualizace Service Pack operačního systému.|
|`productType`|Volitelný parametr. Identifikuje hodnotu typu produktu. Platné hodnoty jsou `server`, `workstation`, a `domainController`. Například pro systém Windows 2000 Professional je `workstation`tato hodnota atributu.|
|`suiteType`|Volitelný parametr. Identifikuje produktovou sadu, která je k dispozici v systému, nebo typ konfigurace systému. Platné hodnoty jsou `backoffice`, `blade`, `datacenter` ,`home`, ,`smallbusinessRestricted`,, a`terminal`. `enterprise` `professional` `smallbusiness` Například pro systém Windows 2000 Professional je `professional`tato hodnota atributu.|

### <a name="dependentassembly"></a>dependentAssembly
 Volitelný parametr. `assemblyIdentity` Obsahuje element. Elementy `dependentOS` `dependency` a `dependentAssembly` se vzájemně vylučují: jeden nebo druhý musí existovat pro prvek, ale ne obojí.

 `dependentAssembly`má následující atributy.

| Atribut | Popis |
|-----------------------| - |
| `dependencyType` | Povinný parametr. Určuje typ závislosti. Platné hodnoty jsou `preprequisite` a `install`. Sestavení je nainstalováno jako součást [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. `install` Aby bylo možné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci nainstalovat, musí být sestavenípřítomnavglobálnímezipamětisestavení(GAC).`prerequisite` |
| `allowDelayedBinding` | Povinný parametr. Určuje, zda lze sestavení načíst programově v době běhu. |
| `group` | Volitelný parametr. `install`Pokud je `dependencyType` atribut nastaven na, označuje pojmenovanou skupinu sestavení, která se instalují pouze na vyžádání. Další informace najdete v tématu [Návod: Stažení sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)<br /><br /> Pokud je nastavena `framework` na `dependencyType` a atribut je nastaven na `prerequisite`, označuje sestavení jako součást .NET Framework. Globální mezipaměť Assemby (GAC) není pro toto sestavení kontrolována při instalaci na .NET Framework 4 a novějších verzích. |
| `codeBase` | Vyžaduje se, `dependencyType` když je atribut nastavený `install`na. Cesta k závislému sestavení Může se jednat o absolutní cestu nebo o cestu relativní vzhledem k základu kódu manifestu. Aby byl manifest sestavení platný, musí být tato cesta platným identifikátorem URI. |
| `size` | Vyžaduje se, `dependencyType` když je atribut nastavený `install`na. Velikost závislého sestavení (v bajtech). |

### <a name="assemblyidentity"></a>assemblyIdentity
 Povinný parametr. Tento prvek je podřízeným `dependentAssembly` prvkem prvku a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Povinný parametr. Určuje název aplikace.|
|`version`|Povinný parametr. Určuje číslo verze aplikace v následujícím formátu:`major.minor.build.revision`|
|`publicKeyToken`|Volitelný parametr. Určuje 16 znaků šestnáctkový řetězec, který představuje posledních 8 bajtů `SHA-1` hodnoty hash veřejného klíče, pod nímž je aplikace nebo sestavení podepsáno. Veřejný klíč, který se používá k podepsání katalogu, musí mít 2048 nebo více bitů.|
|`processorArchitecture`|Volitelný parametr. Určuje procesor. Platné hodnoty jsou `x86` pro 32 – 32bitová okna a `I64` pro 64-bitové okna.|
|`language`|Volitelný parametr. Určuje dva kódy jazyků, například EN-US, sestavení.|

### <a name="hash"></a>hash
 Element je volitelný podřízený `assemblyIdentity` prvek elementu. `hash` `hash` Element nemá žádné atributy.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]používá algoritmus hash pro všechny soubory v aplikaci jako kontrolu zabezpečení, aby se zajistilo, že žádný ze souborů nebyl po nasazení změněn. Není-li prvek zahrnut, tato kontrolu nebude provedena. `hash` Proto vynechání `hash` elementu není doporučeno.

### <a name="dsigtransforms"></a>dsig: transformes
 Element je požadovaný podřízený `hash` prvek elementu. `dsig:Transforms` `dsig:Transforms` Element nemá žádné atributy.

### <a name="dsigtransform"></a>dsig: transformace
 Element je požadovaný podřízený `dsig:Transforms` prvek elementu. `dsig:Transform` `dsig:Transform` Element má následující atributy.

| Atribut | Popis |
|-------------| - |
| `Algorithm` | Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] používá, je. `urn:schemas-microsoft-com:HashTransforms.Identity` |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestMethod` `dsig:DigestMethod` Element má následující atributy.

| Atribut | Popis |
|-------------| - |
| `Algorithm` | Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] používá, je. `http://www.w3.org/2000/09/xmldsig#sha1` |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestValue` `dsig:DigestValue` Element nemá žádné atributy. Jeho textová hodnota je vypočtená hodnota hash pro zadaný soubor.

## <a name="remarks"></a>Poznámky
 Všechna sestavení, která vaše aplikace používá, musí mít `dependency` odpovídající element. Závislá sestavení neobsahují sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC) jako sestavení platformy.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `dependency` elementy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] v manifestu aplikace. Tento příklad kódu je součástí většího příkladu, který je k dispozici v tématu [manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md) .

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

## <a name="see-also"></a>Viz také:
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<element > závislosti](../deployment/dependency-element-clickonce-deployment.md)