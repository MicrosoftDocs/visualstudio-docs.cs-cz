---
title: '&lt;formRegion&gt; – element (vývoj pro Office v sadě Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4fc98e66cd16298839e79f25c95e256f10398c49
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676460"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; – element (vývoj pro Office v sadě Visual Studio)
  `formRegion` Elementu `vstov4` obor názvů identifikuje oblasti formuláře aplikace Microsoft Office Outlook, který je přidružený k doplňku VSTO.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `formRegion` Elementu `vstov4` obor názvů identifikuje oblasti formuláře, který je přidružený doplňku VSTO v Outlooku. Je vyžadován pouze pro aplikaci Outlook doplňků VSTO, které zahrnují oblasti formuláře.  
  
 Může existovat více `formRegion` elementy definované uvnitř `formRegions` – element pro jednoho doplňku VSTO.  
  
 `formRegion` Element má tento atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadováno. Určuje název oblasti formuláře.|  
  
 `formRegion` Element má následující podřízené prvky.  
  
### <a name="messageclass"></a>Třída messageClass  
 `messageClass` Element identifikuje formuláře aplikace Outlook, který je přidružený k oblasti formuláře.  
  
 `messageClass` Element má tento atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadováno. Identifikuje formulář, který je přidružený k oblasti formuláře.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `formRegion` elementu v manifestu aplikace pro Outlook VSTO doplněk nasazeným v rámci [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Existují tři třídy zpráv, které jsou přidružené k této oblasti jeden formulář. Tento příklad kódu je součástí většího příkladu určeného v [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).  
  
```xml  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifesty aplikace pro řešení pro systém Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty nasazení pro řešení pro systém Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce – manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)  
  
  