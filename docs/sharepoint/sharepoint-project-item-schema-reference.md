---
title: Referenční dokumentace schématu položek projektu služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "63007716"
---
# <a name="sharepoint-project-item-schema-reference"></a>Referenční dokumentace schématu položek projektu SharePoint
  Visual Studio používá schéma položek projektu služby SharePoint k ověření obsahu souborů *. spdata* . Soubor *. spdata* určuje obsah a chování položky sharepointového projektu. Další informace o obsahu položek projektu služby SharePoint naleznete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Schéma položky projektu služby SharePoint má název ProjectItemModelSchema. xsd a je ve výchozím nastavení nainstalováno v% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 Kořenový element je element [ProjectItem](../sharepoint/projectitem-element.md) . V následující tabulce jsou popsány všechny prvky definované schématem.

|Element|Popis|
|-------------|-----------------|
|[ExtensionData –](../sharepoint/extensiondata-element.md)|Představuje kolekci vlastních datových položek, které jsou přidruženy k položce projektu služby SharePoint.|
|[ExtensionDataItem –](../sharepoint/extensiondataitem-element.md)|Představuje vlastní datovou položku, která je přidružena k položce projektu služby SharePoint ve formátu klíč/hodnota. Klíč i hodnota musí být řetězce.|
|[FeatureProperties –](../sharepoint/featureproperties-element.md)|Představuje kolekci hodnot vlastností, které jsou součástí funkce při nasazení do služby SharePoint. Po nasazení funkce můžete získat přístup k hodnotám vlastností v kódu.|
|[FeatureProperty –](../sharepoint/featureproperty-element.md)|Představuje vlastní vlastnost, která je součástí funkce při nasazení do služby SharePoint. Po nasazení funkce můžete získat přístup k vlastnosti v kódu.|
|[Soubory](../sharepoint/files-element.md)|Určuje soubory, které mají být nasazeny s položkou projektu služby SharePoint, jako je například soubor prvků funkce nebo výstup projektu.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Představuje položku SharePointového projektu.|
|[ProjectItemFile –](../sharepoint/projectitemfile-element.md)|Představuje soubor služby SharePoint, jako je například soubor prvků funkce, který se má zahrnout do položky projektu při nasazení do služby SharePoint.|
|[ProjectItemFolder –](../sharepoint/projectitemfolder-element.md)|Představuje mapovanou složku.|
|[ProjectOutputFile –](../sharepoint/projectoutputfile-element.md)|Představuje výstup projektu, který má být zahrnut do položky projektu při nasazení do služby SharePoint.|
|[SafeControl –](../sharepoint/safecontrol-element.md)|Představuje ovládací prvek ASPX nebo webovou část, která je označena jako zabezpečená pro všechny uživatele, kteří mají přístup k libovolné stránce ASPX na webu služby SharePoint.|
|[SafeControls –](../sharepoint/safecontrols-element.md)|Představuje kolekci ovládacích prvků ASPX a Webové části, které jsou označeny jako bezpečné pro každého uživatele, aby měli přístup k libovolné stránce ASPX na webu služby SharePoint.|

## <a name="see-also"></a>Viz také
- [Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
