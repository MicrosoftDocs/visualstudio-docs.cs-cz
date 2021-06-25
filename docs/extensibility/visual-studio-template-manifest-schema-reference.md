---
title: Visual Studio schématu manifestu šablony | Microsoft Docs
description: Tento odkaz na schéma popisuje formát souborů manifestu Visual Studio šablon, které jsou generovány Visual Studio šablony projektů nebo položek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905381"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio schématu manifestu šablony
Toto schéma popisuje formát souborů manifestu Visual Studio šablony (*.vstman*), které jsou generovány Visual Studio šablony projektů nebo položek. Schéma také popisuje umístění a další důležité informace o šabloně.

 : Vzhledem k tomu, že existují samostatné adresáře položek a šablon projektů, manifest by nikdy neměl mít kombinaci položek a šablon projektů.

> [!IMPORTANT]
> Tento manifest je k dispozici od Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest – element
 Kořenový element manifestu.

### <a name="attributes"></a>Atributy

- **Verze:** Řetězec představující verzi manifestu šablony. Povinná hodnota.

- **Národní prostředí:** Řetězec představující národní prostředí nebo národní prostředí manifestu šablony. Hodnota národního prostředí se vztahuje na všechny šablony. Pro každé národní prostředí musíte použít samostatný manifest. Nepovinný parametr.

### <a name="child-elements"></a>Podřízené prvky

- **VSTemplateContainer** Volitelné.

- **VSTemplateDir** Volitelné.

### <a name="parent-element"></a>Nadřazený element
 Žádné

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Kontejner elementů manifestu šablony. Manifest má jeden kontejner šablony pro každou šablonu, kterou definuje.

### <a name="attributes"></a>Atributy
 **VSTemplateType:** Řetězcová hodnota, která určuje typ šablony ( `"Project"` `"Item"` , nebo `"ProjectGroup"` ). Vyžadováno

### <a name="child-elements"></a>Podřízené prvky

- **RelativePathOnDisk:** Relativní cesta k souboru šablony na disku. Toto umístění také definuje umístění šablony ve stromu šablon zobrazeném v dialogovém okně Nový **projekt** nebo **Nová** položka. Pro šablony nasazené jako adresář a jednotlivé soubory odkazuje tato cesta na adresář obsahující soubory šablony. Pro šablony nasazené *jako.zip* by tato cesta měla být cesta k tomuto *.zip* souboru.

- **VSTemplateHeader: Element [TemplateData,](../extensibility/templatedata-element-visual-studio-templates.md) který popisuje hlavičku.

### <a name="parent-element"></a>Nadřazený element
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Popisuje adresář, ve kterém se šablona nachází. Manifest může obsahovat více položek **VSTemplateDir,** které poskytují lokalizovaný název a řazení adresářů za účelem řízení jejich vzhledu ve stromu kategorií šablony.

 Vzhledem k jejich návrhu by se **položky VSTemplateDir** měly zobrazovat pouze v manifestech, které nejsou určené pro národní prostředí.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

- **RelativePath**: Cesta k šabloně. Pro každou cestu může být jenom jedna položka, takže první z nich vyhraje pro všechny manifesty.

- **LocalizedName**: **Element NameDescriptionIcon,** který určuje lokalizovaný název. Nepovinný parametr.

- **SortOrder**: Řetězec, který určuje pořadí řazení. Nepovinný parametr.

- **ParentFolderOverrideName:** Přepsané jméno nadřazené složky. Nepovinný parametr. Tento element má atribut **Name,** což je řetězcová hodnota, která určuje název.

### <a name="parent-element"></a>Nadřazený element
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>Popis názvuIcon
 Určuje název a popis, případně pro lokalizované šablony. Viz **LocalizedName** výše.

### <a name="attributes"></a>Atributy

- **Package**: Řetězcová hodnota, která určuje balíček. Nepovinný parametr.

- **ID**: Řetězcová hodnota, která určuje ID. Nepovinný parametr.

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-element"></a>Nadřazený element
 **LocalizedName**

## <a name="examples"></a>Příklady
 Následující kód je příkladem souboru *.vstman šablony* projektu.

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

 Následující kód je příkladem souboru *.vstman šablony* položky.

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
