---
title: Element ProjectItemFolder – | Microsoft Docs
description: Získejte referenční informace o elementu ProjectItemFolder –, který představuje mapovanou složku v odkazu schématu XML položky projektu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d1a5b5086ef90b9d8399a6f0f76bdee77c07288e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950572"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder – element
  Představuje mapovanou složku.

## <a name="syntax"></a>Syntax

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
|**Cíl**|Požadován atribut **xs: String** .<br /><br /> Cesta ke složce v instalaci služby SharePoint, která odpovídá mapované složce, vzhledem k kořenové složce nasazení. Kořenová složka nasazení je určena typem nasazení určeným atributem **Type** .<br /><br /> Další informace naleznete v popisech pro **cestu nasazení** a kořenové vlastnosti **nasazení** položek projektu služby SharePoint v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Požadován atribut **xs: String** .<br /><br /> Typ nasazení mapované složky. Další informace o možných hodnotách naleznete v popisu vlastnosti **typ nasazení** položek projektu služby SharePoint v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Představuje položku SharePointového projektu. Tento prvek je požadovaný kořenový element souboru *. spdata* .|

## <a name="remarks"></a>Poznámky
 Další informace o mapovaných složkách naleznete v tématu [How to: Add and Remove mapované složky](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md)
