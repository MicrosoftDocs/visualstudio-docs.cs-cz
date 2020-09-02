---
title: Nahraditelné parametry | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 165ef1256a0150e0942d85c4f876c8b3f5e15c72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825306"
---
# <a name="replaceable-parameters"></a>Nahraditelné parametry
  Nahraditelné parametry nebo *tokeny*lze použít uvnitř projektových souborů k poskytnutí hodnot pro položky řešení služby SharePoint, jejichž skutečné hodnoty nejsou v době návrhu známy. Jsou obdobou funkcí pro standardní [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokeny šablon. Další informace najdete v tématu [parametry šablony](../ide/template-parameters.md).

## <a name="token-format"></a>Formát tokenu
 Tokeny začínají a končí znakem dolaru ($). Při nasazení jsou všechny použité tokeny nahrazeny skutečnými hodnotami, pokud je projekt zabalen do balíčku řešení služby SharePoint (soubor*WSP* ). Například token **$SharePoint. Package.Name $** může překládat na řetězec "test SharePoint Package".

## <a name="token-rules"></a>Pravidla tokenů
 Následující pravidla platí pro tokeny:

- Tokeny lze zadat kdekoli na řádku.

- Tokeny nemohou zahrnovat více řádků.

- Stejný token lze zadat více než jednou na stejném řádku a ve stejném souboru.

- Na stejném řádku lze zadat různé tokeny.

  Tokeny, které nedodržují tato pravidla, se ignorují a nemají za následek upozornění nebo chybu.

  Nahrazení tokenů hodnotami řetězce je provedeno ihned po transformaci manifestu. Tato náhrada umožňuje uživateli upravovat šablony manifestu pomocí tokenů.

### <a name="token-name-resolution"></a>Překlad názvů tokenů
 Ve většině případů se token překládá na konkrétní hodnotu bez ohledu na to, kde je obsažený. Pokud však token souvisí s balíčkem nebo funkcí, hodnota tokenu závisí na tom, kde je obsažena. Například pokud je funkce v balíčku A, token se `$SharePoint.Package.Name$` přeloží na hodnotu "Package a". Pokud je stejná funkce v balíčku B, pak se `$SharePoint.Package.Name$` přeloží na "Package b".

## <a name="tokens-list"></a>Seznam tokenů
 V následující tabulce jsou uvedeny dostupné tokeny.

|Název|Popis|
|----------|-----------------|
|$SharePoint. Project. FileName $|Název obsahujícího souboru projektu, například, *NewProj. csproj*|
|$SharePoint. Project. FileNameWithoutExtension $|Název obsahujícího souboru projektu bez přípony názvu souboru. Například "NewProj".|
|$SharePoint. Project. AssemblyFullName nemohou mít $|Zobrazovaný název (silný název) obsahující výstupní sestavení projektu.|
|$SharePoint. Project. AssemblyFileName $|Název výstupního sestavení projektu, které obsahuje.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|Název obsahující výstupní sestavení projektu bez přípony názvu souboru.|
|$SharePoint. Project. AssemblyPublicKeyToken $|Token veřejného klíče obsahující výstupní sestavení projektu, který je převeden na řetězec. (16 znaků v šestnáctkovém formátu "X2".)|
|$SharePoint. Package.Name $|Název obsahujícího balíčku|
|$SharePoint. Package. FileName $|Název obsahujícího definičního souboru balíčku.|
|$SharePoint. Package. FileNameWithoutExtension $|Název (bez přípony) balíčku obsahujícího soubor definice.|
|$SharePoint. Package.Id $|ID SharePointu pro obsahující balíček Pokud se funkce používá ve více než jednom balíčku, tato hodnota se změní.|
|$SharePoint. Feature. FileName $|Název definičního souboru obsahujícího funkci, například *Feature1. Feature*.|
|$SharePoint. Feature. FileNameWithoutExtension $|Název souboru definice funkce bez přípony názvu souboru.|
|$SharePoint. Feature. DeploymentPath $|Název složky, která obsahuje funkci v balíčku. Tento token se bude rovnat vlastnosti "cesta nasazení" v Návrháři funkcí. Příkladem je hodnota "Project1_Feature1".|
|$SharePoint. Feature.Id $|ID SharePointu obsahující funkce Tento token, stejně jako u všech tokenů na úrovni funkce, může být používán pouze soubory, které jsou součástí balíčku prostřednictvím funkce, nikoli přímo do balíčku mimo funkci.|
|$SharePoint. ProjectItem.Name $|Název položky projektu (nikoli název souboru), jak získá **ISharePointProjectItem.Name**.|
|$SharePoint. Type. \<GUID> .. AssemblyQualifiedName $|Sestavení kvalifikovaný název typu, který odpovídá [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tokenu. Formát [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] je malý a odpovídá formátu GUID. ToString ("D") (tj. xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint. Type. \<GUID> .. FullName $|Celý název typu, který odpovídá identifikátoru GUID v tokenu. Formát identifikátoru GUID je malými písmeny a odpovídá formátu GUID. ToString ("D") (tj. xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Přidat rozšíření do seznamu přípon náhradních souborů tokenu
 I když mohou být tokeny teoreticky používány jakýmkoli souborem, který patří do položky projektu služby SharePoint, která je součástí balíčku, ve výchozím nastavení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vyhledává tokeny pouze v souborech balíčku, v souborech manifestu a souborech s následujícími příponami:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- WebPart

- DWP

  Tato rozšíření jsou definována `<TokenReplacementFileExtensions>` elementem v souboru Microsoft. VisualStudio. SharePoint. targets, který je umístěn ve složce... \\<Program Files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools složka.

  Do seznamu ale můžete přidat další přípony souborů. Přidejte `<TokenReplacementFileExtensions>` element do jakékoli skupiny vlastností v souboru projektu služby SharePoint, který je definován před \<Import> souborem cílů služby SharePoint.

> [!NOTE]
> Vzhledem k tomu, že náhrada tokenu nastane po zkompilování projektu, neměli byste přidávat přípony souborů pro typy souborů, které jsou kompilovány, například *cs*, *. vb* nebo *. resx*. Tokeny jsou nahrazeny pouze v souborech, které nejsou kompilovány.

 Například chcete-li přidat přípony názvů souborů (*. MyExtension* a *. yourextension*) do seznamu přípon názvů náhradních souborů tokenu, přidejte následující do souboru projektu (*. csproj*):

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 Rozšíření můžete přidat přímo do souboru cílů (*. targets*). Přidání rozšíření však změní seznam rozšíření pro všechny projekty služby SharePoint, které jsou zabaleny v místním systému, nikoli pouze vaše vlastní. Toto rozšíření může být vhodné, pokud jste jediným vývojářem v systému nebo pokud to většina vašich projektů vyžaduje. Vzhledem k tomu, že se jedná o konkrétní systém, tento přístup není přenosný, a proto doporučujeme místo toho přidat jakákoli rozšíření k souboru projektu.

## <a name="see-also"></a>Viz také
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
