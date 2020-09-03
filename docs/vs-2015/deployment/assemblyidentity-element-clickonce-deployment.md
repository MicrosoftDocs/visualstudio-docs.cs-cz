---
title: '&lt;assemblyIdentity – &gt; element (nasazení ClickOnce) | Microsoft Docs'
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155728"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity – &gt; element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifikuje primární sestavení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `assemblyIdentity`Element je povinný. Neobsahuje žádné podřízené elementy a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Povinná hodnota. Určuje uživatelsky čitelný název nasazení pro informativní účely.<br /><br /> Pokud `name` obsahuje speciální znaky, jako například jednoduché nebo dvojité uvozovky, aplikace může selhat při aktivaci.|  
|`version`|Povinná hodnota. Určuje číslo verze sestavení v následujícím formátu: `major.minor.build.revision` .<br /><br /> Tato hodnota musí být zvýšena v aktualizovaném manifestu, aby mohla být aktivována aktualizace aplikace.|  
|`publicKeyToken`|Povinná hodnota. Určuje 16bajtový šestnáctkový řetězec, který představuje posledních 8 bajtů hodnoty hash SHA-1 veřejného klíče, pod kterým je manifest nasazení podepsaný. Veřejný klíč, který se používá k podepsání, musí být 2048 bitů nebo větší.<br /><br /> I když podepisování sestavení je doporučeno, ale nepovinné, tento atribut je povinný. Pokud je sestavení bez znaménka, měli byste zkopírovat hodnotu z sestavení podepsaného svým držitelem nebo použít "fiktivní" hodnotu všech nul.|  
|`processorArchitecture`|Povinná hodnota. Určuje procesor. Platné hodnoty jsou `msil` pro všechny procesory, `x86` pro 32 Windows, `IA64` pro 64-bit Windows a `Itanium` 64 pro procesory Itanium s procesorem Itanium.|  
|`type`|Povinná hodnota. Pro kompatibilitu s technologií souběžné instalace systému Windows. Jediná povolená hodnota je `win32` .|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `assemblyIdentity` prvek v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení. Tento příklad kódu je součástí většího příkladu, který je k dispozici v tématu [manifestu nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> Objekt](../deployment/assemblyidentity-element-clickonce-application.md)
