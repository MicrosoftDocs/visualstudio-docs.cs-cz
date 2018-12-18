---
title: '&lt;vstoruntime –&gt; – element (vývoj pro Office v sadě Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d21e097c0a05dfba2aa15bc41e37441ae02a63e4
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768063"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoruntime –&gt; – element (vývoj pro Office v sadě Visual Studio)
  `vstoRuntime` Element `vstav3` obor názvů obsahuje podporovanou verzi Visual Studio Tools for Office runtime pro konkrétní řešení Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `vstoRuntime` Element je povinná a je v `vstav3` oboru názvů. Pokud řešení Office podporuje dvě verze sady Visual Studio Tools pro systém Office runtime, jsou uvedeny dvě `vstoRuntime` elementy v manifestu aplikace.  
  
 `vstoRuntime` Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`release`|Požadováno. Prodejní verze nástroje sady Visual Studio Tools for Office runtime.|  
|`version`|Požadováno. Číslo verze sady Visual Studio Tools for Office runtime.|  
|`supportUrl`|Volitelné. Propojit k umístění instalace sady Visual Studio Tools for Office runtime.|  
  
 `vstoRuntime` nemá žádné elementy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `vstoRuntime` element v manifestu aplikace pro řešení Office nasadit pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Tento příklad kódu je součástí většího příkladu vztahujícího se v [manifesty aplikací pro řešení Office](../vsto/application-manifests-for-office-solutions.md).  
  
```xml  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>Viz také:  
 [Manifesty aplikace pro řešení pro systém Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce – manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)  
  
  