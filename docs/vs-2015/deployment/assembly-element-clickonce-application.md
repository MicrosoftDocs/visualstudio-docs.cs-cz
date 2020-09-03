---
title: '&lt;Assembly – &gt; element (aplikace ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d619b8b3cd81e5b00fc689077a95ade08f4d7eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183472"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly – &gt; element (aplikace ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element nejvyšší úrovně pro manifest aplikace  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `assembly`Element je kořenový prvek a je povinný. Jeho první obsažený prvek musí být `assemblyIdentity` element. Prvky manifestu musí být v jednom z následujících oborů názvů:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Podřízené elementy sestavení musí být také v těchto oborech názvů, dědění nebo označením.  
  
 `assembly`Element má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`manifestVersion`|Povinná hodnota. `manifestVersion`Atribut musí být nastaven na hodnotu `1.0` .|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `assembly` prvek v manifestu aplikace pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestu aplikace ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## <a name="see-also"></a>Viz také  
 [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assembly> Objekt](../deployment/assembly-element-clickonce-deployment.md)
