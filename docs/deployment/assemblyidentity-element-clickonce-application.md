---
title: '&lt;Vlastnost assemblyIdentity&gt; – Element (aplikace ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89b54c52625578b6ba1f7859654804fa1caaad32
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081267"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;Vlastnost assemblyIdentity&gt; – element (aplikace ClickOnce)
Identifikuje nasazené v aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `assemblyIdentity` Je vyžadován element. Neobsahuje žádné podřízené prvky a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadováno. Určuje název aplikace.<br /><br /> Pokud `Name` obsahuje speciální znaky, jako je například jednoduché nebo dvojité uvozovky, aplikací se pravděpodobně nezdaří k aktivaci.|  
|`Version`|Požadováno. Určuje číslo verze aplikace v následujícím formátu: `major.minor.build.revision`|  
|`publicKeyToken`|Volitelné. Určuje šestnáctkový řetězec 16 znacích představující posledních 8 bajtů `SHA-1` hash hodnoty veřejný klíč, pod kterým je podepsaná aplikace nebo sestavení. Veřejný klíč, který se používá k podepsání katalogu musí být 2 048 bitů nebo vyšší.<br /><br /> I když se podpis sestavení se doporučuje, ale volitelné, tento atribut je vyžadován. Pokud je sestavení bez znaménka, by měl zkopírujte hodnotu z podepsaného sestavení nebo použijte hodnotu "fiktivní" samými nulami.|  
|`processorArchitecture`|Požadováno. Určuje procesor. Platné hodnoty jsou `msil` pro všechny procesory `x86` pro Windows 32-bit `IA64` pro Windows 64-bit, a `Itanium` pro procesory Itanium Intel 64-bit.|  
|`language`|Požadováno. Určuje jazyk kódy dvě součásti (například `en-US`) sestavení. Tento element má `asmv2` oboru názvů. Pokud tento parametr zadán, výchozí hodnota je `neutral`.|  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje `assemblyIdentity` prvek [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace. Tento příklad kódu je součástí většího příkladu určeného v [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Kód  
  
```xml  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Viz také:  
 [ClickOnce – manifest aplikace](../deployment/clickonce-application-manifest.md)   
 [\<Vlastnost assemblyIdentity > – element](../deployment/assemblyidentity-element-clickonce-deployment.md)