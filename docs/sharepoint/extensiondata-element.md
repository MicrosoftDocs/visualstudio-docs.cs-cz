---
title: Element ExtensionData – | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b700239f97153cef94ab1d7010ad16ed9aa6001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546559"
---
# <a name="extensiondata-element"></a>ExtensionData – element
  Představuje kolekci vlastních datových položek, které jsou přidruženy k položce projektu služby SharePoint.

## <a name="syntax"></a>Syntax

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[ExtensionDataItem –](../sharepoint/extensiondataitem-element.md)|Volitelný element.<br /><br /> Představuje vlastní datovou položku, která je přidružena k položce projektu služby SharePoint ve formátu klíč/hodnota. Klíč i hodnota musí být řetězce.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Představuje položku SharePointového projektu. Tento prvek požadovaný kořenový element `.spdata` souboru.|

## <a name="remarks"></a>Poznámky
 Při přidružení vlastních dat k položce projektu služby SharePoint pomocí <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objektu aplikace Visual Studio uloží data do prvku **ExtensionData –** v `.spdata` souboru pro položku projektu. Další informace naleznete v tématu [uložení dat v rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
