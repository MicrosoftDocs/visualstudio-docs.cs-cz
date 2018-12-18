---
title: '&lt;Vlastnost assemblyIdentity&gt; – Element (nasazení ClickOnce) | Dokumentace Microsoftu'
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51ee3ae65c107fc3e6fafbacc3b2e20652ae998d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078024"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;Vlastnost assemblyIdentity&gt; – element (nasazení ClickOnce)
Určuje primární sestavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `assemblyIdentity` Je vyžadován element. Neobsahuje žádné podřízené prvky a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadováno. Určuje popisný název nasazení pro informační účely.<br /><br /> Pokud `name` obsahuje speciální znaky, jako je například jednoduché nebo dvojité uvozovky, aplikací se pravděpodobně nezdaří k aktivaci.|  
|`version`|Požadováno. Určuje číslo verze sestavení, v následujícím formátu: `major.minor.build.revision`.<br /><br /> Tato hodnota musí být zvýšena v aktualizovaném manifestu pro spuštění aktualizace aplikace.|  
|`publicKeyToken`|Požadováno. Určuje šestnáctkový řetězec 16 znacích představující posledních 8 bajtů hodnoty hash SHA-1 veřejný klíč, pod kterým manifest nasazení je podepsán. Veřejný klíč, který se používá k podepsání musí být 2 048 bitů nebo vyšší.<br /><br /> I když se podpis sestavení se doporučuje, ale volitelné, tento atribut je vyžadován. Pokud je sestavení bez znaménka, by měl zkopírujte hodnotu z podepsaného sestavení nebo použijte hodnotu "fiktivní" samými nulami.|  
|`processorArchitecture`|Požadováno. Určuje procesor. Platné hodnoty jsou `msil` pro všechny procesory `x86` pro Windows 32-bit `IA64` pro Windows 64-bit, a `Itanium` pro procesory Itanium Intel 64-bit.|  
|`type`|Požadováno. Z důvodu kompatibility s technologií vedle sebe instalace Windows. Jediná povolená hodnota je `win32`.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `assemblyIdentity` prvek [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu nasazení. Tento příklad kódu je součástí většího příkladu určeného pro [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md) tématu.  
  
```xml  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Viz také:  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [\<Vlastnost assemblyIdentity > – element](../deployment/assemblyidentity-element-clickonce-application.md)