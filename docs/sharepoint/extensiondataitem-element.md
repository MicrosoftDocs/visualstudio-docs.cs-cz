---
title: Element ExtensionDataItem – | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 295ee649cec01e50b237b4fad1798806d460727b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546546"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem – element
  Vlastní datová položka, která je přidružena k položce projektu služby SharePoint, ve formátu klíč/hodnota. Klíč i hodnota musí být řetězce.

## <a name="syntax"></a>Syntax

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**Klíč**|Požadován atribut **xs: String** .<br /><br /> Klíč, který se používá k uložení a načtení datové položky.|
|**Hodnota**|Požadován atribut **xs: String** .<br /><br /> Hodnota datové položky.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ExtensionData –](../sharepoint/extensiondata-element.md)|Představuje kolekci vlastních datových položek, které jsou přidruženy k položce projektu služby SharePoint.|

## <a name="remarks"></a>Poznámky
 Při přidružení vlastních dat k položce projektu služby SharePoint pomocí <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objektu aplikace Visual Studio uloží data do nového prvku **ExtensionDataItem –** v `.spdata` souboru pro položku projektu. Další informace naleznete v tématu [uložení dat v rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
