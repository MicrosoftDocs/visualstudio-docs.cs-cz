---
title: Element SafeControls – | Microsoft Docs
description: Získejte informace o prvku SafeControls –, který obsahuje kolekci ovládacích prvků ASPX nebo webových částí označených jako zabezpečený pro přístup na stránce ASPX webu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3423d1b6efd106ef7f947bd8573dcd1aa548a66
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440672"
---
# <a name="safecontrols-element"></a>SafeControls – element
  Kolekce ovládacích prvků ASPX a Webové části, které jsou označeny jako zabezpečené pro libovolného uživatele pro přístup k libovolné stránce ASPX na webu služby SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[SafeControl –](../sharepoint/safecontrol-element.md)|Volitelný element.<br /><br /> Představuje ovládací prvek ASPX nebo webovou část, která je označena jako zabezpečená pro všechny uživatele, kteří mají přístup k libovolné stránce ASPX na webu služby SharePoint.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Představuje položku SharePointového projektu. Tento prvek vyžaduje kořenový prvek souboru *. spdata* .|

## <a name="remarks"></a>Poznámky
 Další informace o bezpečných ovládacích prvcích najdete [v tématu poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Hosting**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
