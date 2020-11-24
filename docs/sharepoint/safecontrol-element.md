---
title: Element SafeControl – | Microsoft Docs
description: Získat informace o prvku SafeControl –, který představuje ovládací prvek ASPX nebo webovou část označenou jako zabezpečený pro uživatele pro přístup na stránku ASPX webu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36a8b0ed45fbdb8d2dfe8e93a027a47adf407587
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440620"
---
# <a name="safecontrol-element"></a>SafeControl – element
  Představuje ovládací prvek ASPX nebo webovou část, která je označena jako zabezpečená pro všechny uživatele, kteří mají přístup k libovolné stránce ASPX na webu služby SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**Sestavení**|Volitelný atribut **xs: String** .<br /><br /> Název sestavení, ve kterém je definován ovládací prvek ASPX nebo webová část. Ve výchozím nastavení tento atribut používá pro název sestavení nahraditelný parametr **$SharePoint. Project. AssemblyFullName nemohou mít $** . Další informace najdete v tématu [nahraditelných parametrů](../sharepoint/replaceable-parameters.md).|
|**Zabezpečení**|Volitelný atribut **xs: Boolean** .<br /><br /> Určuje, zda je ovládací prvek ASPX nebo webová část zabezpečena pro nedůvěryhodné uživatele, aby k nim měli přístup.|
|**IsSafeAgainstScript**|Volitelný atribut **xs: Boolean** .<br /><br /> Určuje, zda nedůvěryhodní uživatelé mohou zobrazit nebo upravit vlastnosti ovládacího prvku ASPX nebo webové části.|
|**Název**|Volitelný atribut **xs: String** .<br /><br /> Název této položky bezpečného řízení v kolekci.|
|**Hosting**|Volitelný atribut **xs: String** .<br /><br /> Obor názvů ovládacího prvku ASPX nebo webové části.|
|**Popisuje**|Volitelný atribut **xs: String** .<br /><br /> Název typu ovládacího prvku ASPX nebo webové části.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[SafeControls –](../sharepoint/safecontrols-element.md)|Představuje kolekci ovládacích prvků ASPX a Webové části, které jsou označeny jako bezpečné pro každého uživatele, aby měli přístup k libovolné stránce ASPX na webu služby SharePoint.|

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
