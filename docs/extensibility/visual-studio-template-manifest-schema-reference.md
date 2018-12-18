---
title: Odkaz na schéma manifestu šablon sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38581d7c7dd788fef481676283fdc96c8abc96ba
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586303"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Odkaz na schéma manifestu šablony Visual Studio
Toto schéma popisuje formát manifestu šablony sady Visual Studio (*.vstman*) souborů, které jsou generovány pro šablony sady Visual Studio projekt nebo položku. Schéma také popisuje umístění a další důležité informace o šabloně.  
  
 : Protože existují samostatné položky a adresáře šablony projektu, manifest by měl mít nikdy kombinaci šablony položek a projektů.  
  
> [!IMPORTANT]
>  Tento manifest je k dispozici od verze Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest – element  
 Kořenový element v manifestu.  
  
### <a name="attributes"></a>Atributy  
  
-   **Verze**: řetězec představující verze manifestu šablony. Požadováno.  
  
-   **Národní prostředí**: řetězec představující národního prostředí nebo národní prostředí manifestu šablony. Hodnota národního prostředí platí pro všechny šablony. Je nutné použít samostatné manifestu pro každé národní prostředí. Volitelné.  
  
### <a name="child-elements"></a>Podřízené prvky  
  
-   **VSTemplateContainer** volitelné.  
  
-   **VSTemplateDir** volitelné.  
  
### <a name="parent-element"></a>Nadřazený element  
 Žádné  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Kontejner šablony manifestu elementy. Manifest obsahuje jeden kontejner šablony pro každou šablonu, kterou definuje.  
  
### <a name="attributes"></a>Atributy  
 **VSTemplateType**: hodnotu řetězce, která určuje typ šablony (`"Project"`, `"Item"`, nebo `"ProjectGroup"`). Požadováno  
  
### <a name="child-elements"></a>Podřízené prvky  
  
-   **RelativePathOnDisk**: relativní cesta souboru na disku šablony. Toto umístění také definuje umístění šablony ve stromové struktuře šablony je znázorněno **nový projekt** nebo **nová položka** dialogového okna. Pro šablony nasadit jako jednotlivé soubory a adresáře Tato cesta odkazuje na adresář obsahující soubory šablon. Pro šablony nasadit jako *ZIP* soubor, tato cesta musí být cesta k *ZIP* souboru.  
  
-   ** VSTemplateHeader: A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element, který popisuje záhlaví.  
  
### <a name="parent-element"></a>Nadřazený element  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Popisuje adresáře, kde je umístěn šablona. Manifest může obsahovat více **VSTemplateDir** položky k poskytování lokalizovaný název a řazení řazení pro adresáře řídit jejich vzhled ve stromu kategorii šablony.  
  
 Z důvodu jejich návrhu **VSTemplateDir** položky by se měla zobrazit pouze v zadaných manifestů – národní prostředí.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené prvky  
  
-   **RelativePath**: cesta k šabloně. Může existovat jenom jeden záznam za cestu, takže první z nich vyhraje u všech manifestů.  
  
-   **LocalizedName**: A **NameDescriptionIcon** prvek, který určuje lokalizovaný název. Volitelné.  
  
-   **SortOrder –**: řetězec, který určuje pořadí řazení. Volitelné.  
  
-   **ParentFolderOverrideName**: přepsané název nadřazené složky. Volitelné. Tento element nemá **název** atribut, který je hodnota řetězce, který určuje název.  
  
### <a name="parent-element"></a>Nadřazený element  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Určuje název a popis, případně lokalizovaný šablony. Zobrazit **LocalizedName** výše.  
  
### <a name="attributes"></a>Atributy  
  
-   **Balíček**: hodnotu řetězce, která určuje balíček. Volitelné.  
  
-   **ID**: hodnotu řetězce, která určuje ID. Volitelné.  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-element"></a>Nadřazený element  
 **LocalizedName**  
  
## <a name="examples"></a>Příklady  
 Následující kód je příkladem šablony projektu *.vstman* souboru.  
  
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
  
 Následující kód představuje příklad šablony položky *.vstman* souboru.  
  
```xml  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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