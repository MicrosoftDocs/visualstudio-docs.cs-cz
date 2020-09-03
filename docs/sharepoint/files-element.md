---
title: Element Files | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42e919bbe25047da14940203ac86793430aeadde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546507"
---
# <a name="files-element"></a>Files – element
  Určuje soubory, které mají být nasazeny s položkou projektu služby SharePoint, jako jsou například soubory prvků funkce a výstup závislých projektů mimo službu SharePoint.

## <a name="syntax"></a>Syntax

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Typ
 **FileCollectionType**

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectItemFile –](../sharepoint/projectitemfile-element.md)|Volitelný element **ProjectItemFileType** .<br /><br /> Představuje soubor služby SharePoint, jako je například soubor prvků funkce, který se má zahrnout do položky projektu při nasazení do služby SharePoint.|
|[ProjectOutputFile –](../sharepoint/projectoutputfile-element.md)|Volitelný element **ProjectOutputFileType** .<br /><br /> Představuje výstup projektu, který má být zahrnut do položky projektu při nasazení do služby SharePoint.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Představuje položku SharePointového projektu. Tento prvek požadovaný kořenový element `.spdata` souboru.|

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
