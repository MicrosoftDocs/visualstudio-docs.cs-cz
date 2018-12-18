---
title: '&lt;závislost&gt; – Element (nasazení ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: af4b3fc79118e25fb5631de1a4ea4d5897355bf1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214916"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;závislost&gt; – Element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje verzi aplikace k instalaci a umístění manifestu aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `dependency` Je vyžadován element. Nemá žádné atributy. Manifest nasazení může mít více `dependency` elementy.  
  
 `dependency` Element obvykle vyjadřuje v sestaveních obsažených v rámci závislosti pro hlavní aplikaci [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Pokud vaše aplikace Main.exe spotřebuje sestavení nazvané DotNetAssembly.dll, toto sestavení musí být uvedené v oddílu závislosti. Závislost, ale můžete také vyjádřit jiné typy závislostí, například závislosti na konkrétní verzi modulu common language runtime sestavení v globální mezipaměti sestavení (GAC) nebo objekt modelu COM. Protože je technologie nasazení bezdotykový [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nelze zahájit stahování a instalace z těchto typů závislosti, ale nemá zabránit spuštění aplikace Pokud jeden nebo více zadanými závislostmi neexistují.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Požadováno. Tento prvek obsahuje `assemblyIdentity` elementu. V následující tabulce jsou uvedeny atributy `dependentAssembly` podporuje.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`preRequisite`|Volitelné. Určuje, že toto sestavení by již měla existovat v mezipaměti GAC. Platné hodnoty jsou `true` a `false`. Pokud `true`a zadané sestavení v GAC neexistuje, aplikace se nepovedlo spustit.|  
|`visible`|Volitelné. Určuje identitu aplikace nejvyšší úrovně, včetně jejích závislostí. Interně používán [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ke správě úložiště aplikací a aktivace.|  
|`dependencyType`|Požadováno. Vztah mezi touto závislostí a aplikace. Platné hodnoty jsou:<br /><br /> -   `install`. Součást představuje samostatnou instalaci z aktuální aplikace.<br />-   `preRequisite`. Komponenta vyžaduje aktuální aplikace.|  
|`codebase`|Volitelné. Úplná cesta k manifestu aplikace.|  
|`size`|Volitelné. Velikost manifest aplikace v bajtech.|  
  
## <a name="assemblyidentity"></a>Vlastnost assemblyIdentity  
 Požadováno. Tento element je podřízeným prvkem `dependentAssembly` elementu. Obsah `assemblyIdentity` musí být stejné jako nastavení popsané v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace. V následující tabulce jsou uvedeny atributy `assemblyIdentity` elementu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadováno. Určuje název aplikace.|  
|`Version`|Požadováno. Určuje číslo verze aplikace, v následujícím formátu: `major.minor.build.revision`|  
|`publicKeyToken`|Požadováno. Určuje šestnáctkový řetězec 16 znacích představující posledních 8 bajtů hash SHA-1 veřejný klíč, pod kterým je podepsaná aplikace nebo sestavení. Veřejný klíč použitý k podpisu musí být 2 048 bitů nebo vyšší.|  
|`processorArchitecture`|Požadováno. Určuje procesor. Platné hodnoty jsou `x86` pro 32bitová verze Windows a `IA64` pro 64bitová verze Windows.|  
|`Language`|Volitelné. Určuje jazyk kódy dvě části sestavení. Například EN-US, což je zkratka pro angličtinu (US). Výchozí hodnota je `neutral`. Tento element má `asmv2` oboru názvů.|  
|`type`|Volitelné. Pro zpětnou kompatibilitu s Windows – souběžně nainstalovat technologii. Jediná povolená hodnota je `win32`.|  
  
## <a name="hash"></a>hash  
 `hash` Je volitelný podřízený element `file` elementu. `hash` Prvek nemá žádné atributy.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] používá vylepšením hodnota hash všech souborů v aplikaci jako kontrola zabezpečení zajistit, že žádné soubory byly změněny po nasazení. Pokud `hash` element není zahrnut, tato kontrola neproběhne. Proto vynechání `hash` element se nedoporučuje.  
  
## <a name="dsigtransforms"></a>dsig:TRANSFORMS  
 `dsig:Transforms` Je požadovaný podřízený element `hash` elementu. `dsig:Transforms` Prvek nemá žádné atributy.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform` Je požadovaný podřízený element `dsig:Transforms` elementu. V následující tabulce jsou uvedeny atributy `dsig:Transform` elementu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Algorithm`|Algoritmus používaný k výpočtu algoritmu digest pro tento soubor. Aktuálně pouze hodnota používaná metodou [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 `dsig:DigestMethod` Je požadovaný podřízený element `hash` elementu. V následující tabulce jsou uvedeny atributy `dsig:DigestMethod` elementu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Algorithm`|Algoritmus používaný k výpočtu algoritmu digest pro tento soubor. Aktuálně pouze hodnota používaná metodou [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 `dsig:DigestValue` Je požadovaný podřízený element `hash` elementu. `dsig:DigestValue` Prvek nemá žádné atributy. Jeho textová hodnota je vypočítaný algoritmus hash pro zadaný soubor.  
  
## <a name="remarks"></a>Poznámky  
 Manifesty nasazení obvykle mívají jeden `assemblyIdentity` element, který určuje název a verze manifestu aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `dependency` prvek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje závislost na sestavení nainstalovaná v GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje závislost na konkrétní verzi modulu common language runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje závislost operačního systému.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – Manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [\<závislost > – Element](../deployment/dependency-element-clickonce-application.md)



