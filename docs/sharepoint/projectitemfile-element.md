---
title: Element ProjectItemFile – | Microsoft Docs
description: Získejte referenční informace o elementu ProjectItemFile –, který představuje soubor položky projektu v odkazu schématu XML položky projektu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7c6dd7fc46dc8616eddc164bcf2ec801657cb00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955135"
---
# <a name="projectitemfile-element"></a>ProjectItemFile – element
  Představuje soubor služby SharePoint, jako je například soubor prvků funkce, který se má zahrnout do položky projektu při nasazení do služby SharePoint.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Typ
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**Zdroj**|Požadován atribut **xs: String** .<br /><br /> Název souboru, který má být nasazen s položkou projektu.|
|**Cíl**|Volitelný atribut **xs: String** .<br /><br /> Cesta, kam se soubor nasadí na SharePointu, vzhledem k kořenové složce nasazení Kořenová složka nasazení je určena typem nasazení určeným atributem **Type** . Pokud **cílový** atribut není zadán, soubor bude nasazen do složky s názvem zadaným ve **zdrojovém** atributu.<br /><br /> Další informace naleznete v popisech pro **cestu nasazení** a kořenové vlastnosti **nasazení** položek projektu služby SharePoint v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Požadován atribut **xs: String** .<br /><br /> Typ nasazení souboru. Další informace o možných hodnotách naleznete v popisu vlastnosti **typ nasazení** položek projektu služby SharePoint v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Soubory](../sharepoint/files-element.md)|Určuje soubory, které mají být zahrnuty do položky projektu služby SharePoint, když jsou nasazeny do služby SharePoint.|

## <a name="remarks"></a>Poznámky
 Soubory SharePointu, které jsou obvykle odkazovány v prvcích **ProjectItemFile –** , zahrnují soubory prvků funkce (*Elements.xml*), soubory schématu pro definice seznamu (*Schema.xml*) a soubory definice webových částí pro webové části (*. WebPart*).

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|Ne|

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
