---
title: ProjectItemFolder – Element | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54d47165117b88041346e9b666db8db17a20ddb9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120364"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder – element
  Představuje mapované složky.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Typ  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Cíl**|Požadované **xs: řetězec** atribut.<br /><br /> Cesta ke složce v instalaci služby SharePoint, které mapované složky odpovídá relativní vzhledem ke kořenové složce nasazení. Nasazení kořenové složky je určen podle typu nasazení určeného **typ** atribut.<br /><br /> Další informace najdete v popisech pro **Cesta nasazení** a **nasazení kořenové** projektu služby SharePoint položky v [řešení služby SharePoint vyvíjet](../sharepoint/developing-sharepoint-solutions.md).|  
|**Typ**|Požadované **xs:string** atribut.<br /><br /> Typ nasazení pro mapované složky. Další informace o možných hodnot, viz popis **typ nasazení** vlastnosti položky projektu služby SharePoint v [řešení služby SharePoint vyvíjet](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Podřízené prvky
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ProjectItem –](../sharepoint/projectitem-element.md)|Představuje položky projektu služby SharePoint. Tento element má požadovaný kořenový element *.spdata* souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o mapované složky najdete v tématu [postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Informace o elementu
  
|||  
|-|-|  
|**Namespace**|http<nolink>: //schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|  
|**Název schématu**|Schéma položky projektu SharePoint|  
|**Ověření souboru**|ProjectItemModelSchema.xsd|  
|**Nesmí být prázdné**|Ne|  
  
## <a name="see-also"></a>Viz také:
 [Referenční dokumentace schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
