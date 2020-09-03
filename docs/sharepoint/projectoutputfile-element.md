---
title: Element ProjectOutputFile – | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12f399b7a09c18c77482475575ca387a11955762
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542386"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile – element
  Představuje výstup samostatného projektu, který má být zahrnut do položky projektu při nasazení do služby SharePoint.

## <a name="syntax"></a>Syntax

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Typ
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**ProjectId.**|Požadován atribut **xs: String** .<br /><br /> Identifikátor GUID závislého projektu, který obsahuje výstup, který chcete zahrnout. To odpovídá prvku **ProjectGuid** v souboru závislého projektu.|
|**ProjectPath**|Požadován atribut **xs: String** .<br /><br /> Relativní cesta, včetně názvu souboru projektu, závislého projektu, který má výstup, který chcete zahrnout. Tato cesta je relativní vzhledem ke kořenové složce projektu služby SharePoint, který obsahuje položku SharePointového projektu.|
|**Cílové**|Volitelný atribut **xs: String** .<br /><br /> Cesta, kam má být na SharePointovém serveru nasazený výstup závislého projektu, je relativní vzhledem ke kořenové složce nasazení. Kořenová složka nasazení je určena typem nasazení určeným atributem **Type** .<br /><br /> Další informace naleznete v popisech pro **cestu nasazení** a kořenové vlastnosti **nasazení** položek projektu služby SharePoint v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Požadován atribut **xs: String** .<br /><br /> Typ nasazení, který má být použit pro výstup závislého projektu. Další informace o možných hodnotách naleznete v popisu vlastnosti **typ nasazení** položek projektu služby SharePoint v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Soubory](../sharepoint/files-element.md)|Určuje soubory, které mají být zahrnuty do položky projektu služby SharePoint, když jsou nasazeny do služby SharePoint.|

## <a name="remarks"></a>Poznámky
 Použijte element **ProjectOutputFile –** , chcete-li zahrnout výstup projektu do nasazení položky projektu služby SharePoint. Můžete zadat jiný projekt nebo stejný projekt, který obsahuje položku projektu. Další informace najdete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
