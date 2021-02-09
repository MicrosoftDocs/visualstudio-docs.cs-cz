---
title: Element Files | Microsoft Docs
description: Zobrazení referenčních informací o elementu Files, což je prvek ve schématu položky projektu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 653e48a2e9b6a68db94fd66660da85f4dec20927
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876644"
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
