---
title: Referenční příručka pro manifest šablony sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697984"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Odkaz na schéma manifestu šablony sady Visual Studio
Toto schéma popisuje formát manifestu šablony sady Visual Studio (*.vstman*) soubory, které jsou generovány pro projekt Visual Studio nebo šablony položek. Schéma také popisuje umístění a další relevantní informace o šabloně.

 : Vzhledem k tomu, že existují samostatné adresáře položek a šablon projektu, manifest by nikdy neměl mít kombinaci šablon položek a projektů.

> [!IMPORTANT]
> Tento manifest je k dispozici od visual studia 2017.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest prvek
 Kořenový prvek manifestu.

### <a name="attributes"></a>Atributy

- **Verze**: Řetězec představující verzi manifestu šablony. Povinná hodnota.

- **Národní prostředí**: Řetězec představující národní prostředí nebo národní prostředí manifestu šablony. Hodnota národního prostředí platí pro všechny šablony. Pro každé národní prostředí je nutné použít samostatný manifest. Nepovinný parametr.

### <a name="child-elements"></a>Podřízené prvky

- **Kontejner VSTemplate** Volitelné.

- **VSTemplateDir** Volitelné.

### <a name="parent-element"></a>Nadřazený prvek
 Žádné.

## <a name="vstemplatecontainer"></a>Kontejner VSTemplate
 Kontejner prvků manifestu šablony. Manifest má jeden kontejner šablony pro každou šablonu, kterou definuje.

### <a name="attributes"></a>Atributy
 **VSTemplateType**: Hodnota řetězce, která určuje typ`"Project"` `"Item"`šablony `"ProjectGroup"`( , , nebo ). Požaduje se

### <a name="child-elements"></a>Podřízené prvky

- **RelativePathOnDisk**: Relativní cesta k souboru šablony na disku. Toto umístění také definuje umístění šablony ve stromu šablony zobrazeném v dialogovém okně **Nový projekt** nebo **Nová položka.** U šablon nasazených jako adresář a jednotlivé soubory odkazuje tato cesta na adresář obsahující soubory šablon. U šablon nasazených jako soubor *ZIP* by tato cesta měla být cestou k souboru *ZIP.*

- **VSTemplateHeader: Element [TemplateData,](../extensibility/templatedata-element-visual-studio-templates.md) který popisuje hlavičku.

### <a name="parent-element"></a>Nadřazený prvek
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Popisuje adresář, ve kterém je šablona umístěna. Manifest může obsahovat více položek **VSTemplateDir** poskytnout lokalizovaný název a řazení pro adresáře řídit jejich vzhled ve stromu kategorií šablony.

 Vzhledem k jejich návrhu by se položky **VSTemplateDir** měly zobrazovat pouze v nenárodních manifestech.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky

- **RelativePath**: Cesta k šabloně. Na cestu může být pouze jedna položka, takže první z nich vyhraje pro všechny manifesty.

- **LocalizedName**: A **NameDescriptionIcon** element, který určuje lokalizovaný název. Nepovinný parametr.

- **SortOrder**: Řetězec, který určuje pořadí řazení. Nepovinný parametr.

- **ParentFolderOverrideName**: Přepsaný název nadřazené složky. Nepovinný parametr. Tento prvek má **Name** atribut, což je hodnota řetězce, který určuje název.

### <a name="parent-element"></a>Nadřazený prvek
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NázevDescriptionIcon
 Určuje název a popis, případně pro lokalizované šablony. Viz **LocalizedName** výše.

### <a name="attributes"></a>Atributy

- **Balíček**: Hodnota řetězce, která určuje balíček. Nepovinný parametr.

- **ID**: Hodnota řetězce, která určuje ID. Nepovinný parametr.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-element"></a>Nadřazený prvek
 **Lokalizovaný název**

## <a name="examples"></a>Příklady
 Následující kód je příkladem souboru šablony projektu *.vstman.*

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

 Následující kód je příkladem souboru *.vstman* šablony položky.

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
