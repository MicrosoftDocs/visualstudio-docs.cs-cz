---
title: '&lt;Dependency – &gt; element (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187774"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Dependency – &gt; element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje verzi aplikace, která se má nainstalovat, a umístění manifestu aplikace.  
  
## <a name="syntax"></a>Syntax  
  
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
 `dependency`Element je povinný. Nemá žádné atributy. Manifest nasazení může mít více `dependency` elementů.  
  
 `dependency`Element obvykle vyjadřuje závislosti pro hlavní aplikaci na sestaveních obsažených v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci. Pokud vaše aplikace Main.exe spotřebovává sestavení s názvem DotNetAssembly.dll, pak toto sestavení musí být uvedené v části závislosti. Závislost může však také zamezit jiné typy závislostí, například závislosti na konkrétní verzi modulu CLR (Common Language Runtime), sestavení v globální mezipaměti sestavení (GAC) nebo objektu COM. Vzhledem k tomu, že se jedná o technologii nasazení bez dotykového nasazení, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nelze zahájit stahování a instalaci těchto typů závislostí, ale zabrání spuštění aplikace, pokud jedna nebo více zadaných závislostí neexistuje.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Povinná hodnota. Tento element obsahuje `assemblyIdentity` element. V následující tabulce jsou uvedeny atributy, které `dependentAssembly` podporuje.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`preRequisite`|Nepovinný parametr. Určuje, že toto sestavení by již mělo existovat v globální mezipaměti sestavení (GAC). Platné hodnoty jsou `true` a `false` . Pokud `true` a zadané sestavení v globální mezipaměti sestavení (GAC) neexistuje, spuštění aplikace se nezdařilo.|  
|`visible`|Nepovinný parametr. Identifikuje identitu aplikace nejvyšší úrovně, včetně jejích závislostí. Interně [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se používá ke správě úložiště a Aktivace aplikací.|  
|`dependencyType`|Povinná hodnota. Vztah mezi touto závislostí a aplikací. Platné hodnoty jsou:<br /><br /> -   `install`. Součást představuje samostatnou instalaci z aktuální aplikace.<br />-   `preRequisite`. Aktuální aplikace vyžaduje komponentu.|  
|`codebase`|Nepovinný parametr. Úplná cesta k manifestu aplikace.|  
|`size`|Nepovinný parametr. Velikost manifestu aplikace v bajtech.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Povinná hodnota. Tento prvek je podřízeným `dependentAssembly` prvkem elementu. Obsah `assemblyIdentity` musí být stejný, jak je popsáno v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace. V následující tabulce jsou uvedeny atributy `assemblyIdentity` prvku.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Určuje název aplikace.|  
|`Version`|Povinná hodnota. Určuje číslo verze aplikace v následujícím formátu: `major.minor.build.revision`|  
|`publicKeyToken`|Povinná hodnota. Určuje 16bajtový šestnáctkový řetězec, který představuje posledních 8 bajtů hodnoty hash SHA-1 veřejného klíče, pod nímž je aplikace nebo sestavení podepsáno. Veřejný klíč, který se používá k podepsání, musí být 2048 bitů nebo větší.|  
|`processorArchitecture`|Povinná hodnota. Určuje mikroprocesor. Platné hodnoty jsou `x86` pro 32 – 32bitová okna a `IA64` pro 64-bitové okna.|  
|`Language`|Nepovinný parametr. Určuje dvě části kódů jazyka sestavení. Například EN-US, který představuje angličtinu (USA). Výchozí formát je `neutral`. Tento prvek je v `asmv2` oboru názvů.|  
|`type`|Nepovinný parametr. Pro zpětnou kompatibilitu s technologií souběžné instalace systému Windows. Jediná povolená hodnota je `win32` .|  
  
## <a name="hash"></a>hash  
 `hash`Element je volitelný podřízený `file` prvek elementu. `hash`Element nemá žádné atributy.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] používá algoritmus hash algoritmu všech souborů v aplikaci jako kontrolu zabezpečení, aby se zajistilo, že žádný ze souborů nebyl po nasazení změněn. Není `hash` -li prvek zahrnut, tato kontrolu nebude provedena. Proto vynechání `hash` elementu není doporučeno.  
  
## <a name="dsigtransforms"></a>dsig: transformes  
 `dsig:Transforms`Element je požadovaný podřízený `hash` prvek elementu. `dsig:Transforms`Element nemá žádné atributy.  
  
## <a name="dsigtransform"></a>dsig: transformace  
 `dsig:Transform`Element je požadovaný podřízený `dsig:Transforms` prvek elementu. V následující tabulce jsou uvedeny atributy `dsig:Transform` prvku.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Algorithm`|Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou používá, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`Element je požadovaný podřízený `hash` prvek elementu. V následující tabulce jsou uvedeny atributy `dsig:DigestMethod` prvku.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Algorithm`|Algoritmus použitý k výpočtu hodnoty Digest pro tento soubor. Aktuálně jediná hodnota, kterou používá, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 `dsig:DigestValue`Element je požadovaný podřízený `hash` prvek elementu. `dsig:DigestValue`Element nemá žádné atributy. Jeho textová hodnota je vypočtená hodnota hash pro zadaný soubor.  
  
## <a name="remarks"></a>Poznámky  
 Manifesty nasazení obvykle mají jediný `assemblyIdentity` element, který identifikuje název a verzi manifestu aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `dependency` prvek v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení.  
  
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
 Následující příklad kódu určuje závislost na sestavení, které je již nainstalováno v globální mezipaměti sestavení (GAC).  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje závislost na konkrétní verzi modulu CLR (Common Language Runtime).  
  
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
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> Objekt](../deployment/dependency-element-clickonce-application.md)
