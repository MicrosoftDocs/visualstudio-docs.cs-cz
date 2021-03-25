---
title: Referenční informace schématu manifestu šablony sady Visual Studio | Microsoft Docs
description: Tento odkaz na schéma popisuje formát souborů manifestu šablon sady Visual Studio, které jsou generovány pro projekty aplikace Visual Studio nebo šablony položek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 033e735b93a534164d96cf47d6412c609525ad8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062496"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referenční dokumentace schématu manifestu šablony sady Visual Studio
Toto schéma popisuje formát souborů manifestu šablony sady Visual Studio (*. vstman*), které jsou generovány pro projekty aplikace Visual Studio nebo šablony položek. Schéma také popisuje umístění a další důležité informace o této šabloně.

 : Protože existují samostatné adresáře šablon položek a projektů, manifest by nikdy neměl obsahovat kombinaci položek a šablon projektů.

> [!IMPORTANT]
> Tento manifest je k dispozici od začátku v aplikaci Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Element VSTemplateManifest
 Kořenový prvek manifestu.

### <a name="attributes"></a>Atributy

- **Verze**: řetězec představující verzi manifestu šablony. Povinná hodnota.

- **Locale**: řetězec představující národní prostředí nebo národní prostředí manifestu šablony. Hodnota národního prostředí se vztahuje na všechny šablony. Je nutné použít samostatný manifest pro každé národní prostředí. Nepovinný parametr.

### <a name="child-elements"></a>Podřízené prvky

- **VSTemplateContainer** Volitelné.

- **VSTemplateDir** Volitelné.

### <a name="parent-element"></a>Nadřazený element
 Žádné

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Kontejner prvků manifestu šablony. Manifest má jeden kontejner šablon pro každou šablonu, kterou definuje.

### <a name="attributes"></a>Atributy
 **VSTemplateType**: hodnota řetězce, která určuje typ šablony ( `"Project"` , `"Item"` nebo `"ProjectGroup"` ). Vyžadováno

### <a name="child-elements"></a>Podřízené prvky

- **RelativePathOnDisk**: relativní cesta k souboru šablony na disku. Toto umístění také definuje umístění šablony ve stromu šablony zobrazeném v dialogovém okně **Nový projekt** nebo **Nová položka** . Pro šablony nasazené jako adresář a jednotlivé soubory odkazuje tato cesta na adresář obsahující soubory šablon. V případě šablon nasazených jako soubor *. zip* by tato cesta měla být cesta k souboru *. zip* .

- * * VSTemplateHeader: element [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) , který popisuje hlavičku.

### <a name="parent-element"></a>Nadřazený element
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Popisuje adresář, ve kterém je šablona umístěna. Manifest může obsahovat více **VSTemplateDir** záznamů pro poskytnutí lokalizovaného názvu a řazení pro adresáře pro kontrolu jejich vzhledu ve stromu kategorií šablon.

 Z důvodu jejich návrhu by se položky **VSTemplateDir** měly zobrazit pouze v manifestech, které nejsou zadány národním prostředím.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

- **RelativePath**: cesta k šabloně. Pro každou cestu může existovat jenom jedna položka, takže první z nich se načte pro všechny manifesty.

- **Lokalizovaný** název: element **NameDescriptionIcon** , který určuje lokalizovaný název. Nepovinný parametr.

- **Pořadí**: řetězec, který určuje pořadí řazení. Nepovinný parametr.

- **ParentFolderOverrideName**: přejmenovaný název nadřazené složky. Nepovinný parametr. Tento prvek má atribut **Name** , což je řetězcová hodnota, která určuje název.

### <a name="parent-element"></a>Nadřazený element
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Určuje název a popis, případně pro lokalizované šablony. Viz **lokalizovaný** symbol výše.

### <a name="attributes"></a>Atributy

- **Balíček**: řetězcová hodnota, která určuje balíček. Nepovinný parametr.

- **ID**: hodnota řetězce, která určuje ID. Nepovinný parametr.

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-element"></a>Nadřazený element
 **Lokalizovaný**

## <a name="examples"></a>Příklady
 Následující kód je příkladem souboru *. vstman* šablony projektu.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Následující kód je příkladem souboru template *. vstman* položky.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
