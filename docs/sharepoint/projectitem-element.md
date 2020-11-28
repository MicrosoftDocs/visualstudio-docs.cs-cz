---
title: ProjectItem – element | Microsoft Docs
description: Získejte referenční informace o elementu ProjectItem, který představuje položku SharePointového projektu v odkazu schématu XML položky projektu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e211aa44b1402d6667fc3e02ca7e271a29c3ec7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305055"
---
# <a name="projectitem-element"></a>ProjectItem – element
  Představuje položku SharePointového projektu. Tento prvek vyžaduje kořenový prvek souboru *. spdata* .

## <a name="syntax"></a>Syntax

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**DefaultFile**|Volitelný atribut **xs: String** .<br /><br /> Relativní cesta, včetně názvu souboru, souboru, který se otevře v editoru sady Visual Studio při otevření položky SharePointového projektu v **Průzkumník řešení**. Cesta je relativní ze složky, která obsahuje soubor *. spdata* .|
|**FeatureReceiverClass**|Volitelný atribut **xs: String** .<br /><br /> Plně kvalifikovaný název třídy příjemce funkce pro tuto položku SharePointového projektu. Další informace o přijímačích funkcí naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Volitelný atribut **xs: String** .<br /><br /> Určuje plně kvalifikovaný název sestavení, které definuje přijímač funkce pro tuto položku SharePointového projektu. Další informace o přijímačích funkcí naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Další informace o plně kvalifikovaných názvech sestavení naleznete v tématu [názvy sestavení](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Volitelný atribut **xs: String** .<br /><br /> Určuje úrovně důvěryhodnosti, které podporuje tato položka SharePointového projektu. Tato hodnota může být jeden z následujících řetězců: Sandboxed, FullTrust nebo ALL. Hodnota All určuje jak izolovaný prostor, tak i FullTrust.<br /><br /> Ve vlastním typu položky projektu služby SharePoint odpovídá hodnota tohoto atributu hodnotě, kterou přiřadíte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> vlastnosti v implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Zadáte-li pro tento atribut jinou hodnotu, aplikace Visual Studio přepíše hodnotu tak, aby určovala stejnou úroveň důvěryhodnosti, kterou zadáte ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Vlastnosti.|
|**SupportedDeploymentScopes**|Volitelný atribut **xs: String** .<br /><br /> Určuje rozsahy nasazení, které tato položka SharePointového projektu podporuje. Tato hodnota je řetězec oddělený čárkami, který se skládá z jednoho nebo více následujících řetězců: farma, web, web, Webová aplikace nebo balíček. Příklad: `Web, Site`<br /><br /> Ve vlastním typu položky projektu služby SharePoint odpovídá hodnota tohoto atributu hodnotě, kterou přiřadíte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> vlastnosti v implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Zadáte-li pro tento atribut jinou hodnotu, aplikace Visual Studio přepíše hodnotu tak, aby určovala stejnou úroveň důvěryhodnosti, kterou zadáte ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Vlastnosti.|
|**Typ**|Požadován atribut **xs: String** .<br /><br /> Identifikátor položky projektu služby SharePoint. Ve vlastním typu položky projektu služby SharePoint je identifikátor řetězcem, který předáte do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Další informace naleznete v tématu [How to: define a Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Seznam identifikátorů pro předdefinované položky projektu služby SharePoint, které jsou součástí sady Visual Studio, naleznete v tématu [extend and SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[ExtensionData –](../sharepoint/extensiondata-element.md)|Volitelný element.<br /><br /> Představuje kolekci vlastních datových položek, které jsou přidruženy k položce projektu služby SharePoint.<br /><br /> Můžete zahrnout pouze jeden prvek **ExtensionData –** .|
|[FeatureProperties –](../sharepoint/featureproperties-element.md)|Volitelný element.<br /><br /> Představuje kolekci hodnot vlastností, které jsou součástí funkce při nasazení do služby SharePoint.<br /><br /> Můžete zahrnout pouze jeden prvek **FeatureProperties –** .|
|[Soubory](../sharepoint/files-element.md)|Volitelný element **FileCollectionType** .<br /><br /> Určuje soubory, které mají být nasazeny s položkou projektu služby SharePoint, jako jsou například soubory prvků funkce a výstup závislých projektů mimo službu SharePoint.<br /><br /> Zahrňte buď **soubory** , nebo element **ProjectItemFolder –** , ale ne obojí.|
|[ProjectItemFolder –](../sharepoint/projectitemfolder-element.md)|Volitelný element **ProjectItemFolderType** .<br /><br /> Představuje mapovanou složku.<br /><br /> Zahrňte buď **soubory** , nebo element **ProjectItemFolder –** , ale ne obojí.|
|[SafeControls –](../sharepoint/safecontrols-element.md)|Volitelný element.<br /><br /> Představuje kolekci ovládacích prvků ASPX a Webové části, které jsou označeny jako bezpečné pro každého uživatele, aby měli přístup k libovolné stránce ASPX na webu služby SharePoint.<br /><br /> Můžete zahrnout pouze jeden prvek **SafeControls –** .|

### <a name="parent-elements"></a>Nadřazené prvky
 Žádné

## <a name="element-information"></a>Informace o elementu

|Vlastnost|Hodnota|
|-|-|
|**Obor názvů**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Název schématu**|Schéma položek projektu služby SharePoint|
|**Soubor ověření**|ProjectItemModelSchema. xsd|
|**Může být prázdné**|No|

## <a name="see-also"></a>Viz také
[Rseference schématu položek projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
