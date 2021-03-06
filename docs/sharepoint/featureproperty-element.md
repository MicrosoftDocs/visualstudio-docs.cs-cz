---
title: Element FeatureProperty – | Microsoft Docs
description: Zobrazení referenčních informací o prvku FeatureProperty –, což je prvek ve schématu položky projektu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070866b9dd14d974eb976b22bf7a79907e2c5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876664"
---
# <a name="featureproperty-element"></a>FeatureProperty – element
  Představuje vlastní vlastnost, která je součástí funkce při nasazení do služby SharePoint. Po nasazení funkce můžete získat přístup k vlastnosti v kódu.

## <a name="syntax"></a>Syntax

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**Klíč**|Požadován atribut **xs: String** .<br /><br /> Klíč, který se používá k ukládání a načítání hodnoty vlastnosti. Každá vlastnost musí mít klíč, který je jedinečný v rámci této funkce.|
|**Hodnota**|Požadován atribut **xs: String** .<br /><br /> Hodnota vlastnosti|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[FeatureProperties –](../sharepoint/featureproperties-element.md)|Představuje kolekci hodnot vlastností, které jsou součástí funkce při nasazení do služby SharePoint.|

## <a name="remarks"></a>Poznámky
 Další informace o vlastnostech funkcí naleznete v tématu [poskytnutí informací o balíčku a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
