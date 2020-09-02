---
title: '&lt;assemblyIdentity – &gt; element (aplikace ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bde22809af69071f5484e25717a5aea7d78a603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428531"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity – &gt; element (aplikace ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifikuje aplikaci nasazenou v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `assemblyIdentity`Element je povinný. Neobsahuje žádné podřízené elementy a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Určuje název aplikace.<br /><br /> Pokud `Name` obsahuje speciální znaky, jako například jednoduché nebo dvojité uvozovky, aplikace může selhat při aktivaci.|  
|`Version`|Povinná hodnota. Určuje číslo verze aplikace v následujícím formátu: `major.minor.build.revision`|  
|`publicKeyToken`|Nepovinný parametr. Určuje 16 znaků šestnáctkový řetězec, který představuje posledních 8 bajtů `SHA-1` hodnoty hash veřejného klíče, pod nímž je aplikace nebo sestavení podepsáno. Veřejný klíč, který se používá k podepsání katalogu, musí být 2048 bitů nebo větší.<br /><br /> I když podepisování sestavení je doporučeno, ale nepovinné, tento atribut je povinný. Pokud je sestavení bez znaménka, měli byste zkopírovat hodnotu z sestavení podepsaného svým držitelem nebo použít "fiktivní" hodnotu všech nul.|  
|`processorArchitecture`|Povinná hodnota. Určuje procesor. Platné hodnoty jsou `msil` pro všechny procesory, `x86` pro 32 Windows, `IA64` pro 64-bit Windows a `Itanium` 64 pro procesory Itanium s procesorem Itanium.|  
|`language`|Povinná hodnota. Identifikuje kódy jazyků dvou částí (například `en-US` ) sestavení. Tento prvek je v `asmv2` oboru názvů. Je-li tento parametr zadán, je použita výchozí hodnota `neutral` .|  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje `assemblyIdentity` prvek v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestu aplikace ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Kód  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity> Objekt](../deployment/assemblyidentity-element-clickonce-deployment.md)
