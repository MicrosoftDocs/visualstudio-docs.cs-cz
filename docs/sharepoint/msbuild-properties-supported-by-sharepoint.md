---
title: Vlastnosti nástroje MSBuild podporované službou SharePoint | Microsoft Docs
description: Přečtěte si seznam názvů a popisů vlastností MSBuild, které jsou podporovány nástrojem a jsou specifické pro službu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20458cc7047e913e13f4594380d4b4946b44ec17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938509"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Vlastnosti nástroje MsBuild podporované službou SharePoint
  Všechny [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastnosti definované v souboru Microsoft. VisualStudio. SharePoint. targets, souboru projektu nebo uživatelském souboru projektu lze použít v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektech služby SharePoint. Kromě běžných [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastností dodaných projektem definuje SharePoint další vlastnosti, které jsou specifické pro projekty služby SharePoint.

 Seznam společných [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastností najdete v tématu [běžné vlastnosti projektu MSBuild](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Úplný seznam vlastností podporovaných vaším programovacím jazykem najdete v souboru *. targets* , souboru projektu (*. csproj* nebo *. vbproj*) nebo v uživatelském souboru projektu (*csproj. User* nebo *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Vlastnosti nástroje MsBuild specifické pro službu SharePoint
 V následující tabulce jsou uvedeny [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastnosti, které platí konkrétně pro projekty služby SharePoint v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Existují další vlastnosti, ale jsou pro interní použití.

|Název vlastnosti|Description|
|-------------------|-----------------|
|SharePointSiteUrl|Řetězec, který představuje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] web služby SharePoint.|
|SandboxedSolution|Logická hodnota, která označuje, zda je řešení řešením v izolovaném prostoru.|
|ActiveDeploymentConfiguration|Konfigurace aktivního nasazení.|
|IncludeAssemblyInPackage|Logická hodnota, která určuje, zda je sestavení obsaženo v souboru balíčku.|
|PreDeploymentCommand|Řetězcová hodnota, která představuje příkaz, který se má provést v kroku příkazu před nasazením.|
|PostDeploymentCommand|Řetězcová hodnota, která představuje příkaz, který má být proveden v kroku příkazu po nasazení.|
|CustomBeforeSharePointTargets|Řetězec, který představuje cestu k [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] souboru cílů. Pokud soubor cílů existuje a je definován, je importován před daty cíle služby SharePoint. Tato vlastnost umožňuje přizpůsobit proces balíčku Předdefinováním vlastností, které se týkají balíčku, aniž byste museli měnit daný soubor cílů služby SharePoint. Tento soubor se ale přesto vztahuje na všechny projekty SharePoint.|
|CustomAfterSharePointTargets|Řetězec, který představuje cestu k [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] souboru cílů. Pokud soubor cílů existuje a je definován, je importován po všech datech cíle služby SharePoint. Tato vlastnost umožňuje přizpůsobit proces balíčku přepsáním vlastností a cílů souvisejících s balíčkem, aniž byste museli upravovat soubory odeslaných cílů služby SharePoint, a přesto se tento soubor cíle vztahuje na všechny projekty služby SharePoint.|
|LayoutPath|Řetězec, který představuje kořenový adresář, ve kterém jsou jednotlivé soubory, které mají být zabaleny, dočasně umístěny před jejich přidáním do souboru *. wsp* . Tato cesta může být užitečná, když přepíšete cíle BeforeLayout a AfterLayout na přidávání, odebírání nebo úpravu souborů, které mají být zabaleny, protože ji můžete použít k úpravě obsahu souboru *WSP* .|
|BasePackagePath|Řetězec, který představuje složku, do které je balíček umístěn. Tato hodnota používá výstupní adresář projektu, například Bin\Debug..|
|PackageExtension|Řetězec, který představuje příponu názvu souboru, který se má připojit k balíčku. Výchozí hodnota je WSP.|
|AssemblyDeploymentTarget|Řetězec představující umístění, kde je sestavení projektu nasazeno na serveru SharePoint. Jeho hodnota je buď GlobalAssemblyCache (výchozí), nebo WebApplication. Tuto vlastnost lze nastavit také v okno Vlastnosti.|
|PackageWithValidation|Logická hodnota, která určuje, zda je ověřování provedeno před balením. Tato vlastnost umožňuje ignorovat chyby ověřování při vytváření balíčků.|
|ValidatePackageDependsOn|Řetězec, který definuje další cíle, které se mají provést před cílem ValidatePackage|
|TokenReplacementFileExensions|Řetězec definující soubory, které mají své tokeny nahrazeny během balení.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Použití vlastností MsBuild na stránce vlastností
 V případě flexibility namísto použití pevně zakódovaných řetězců v polích příkazového **řádku před nasazením** a **příkazového řádku po nasazení** na stránce vlastností služby SharePoint můžete jako argumenty použít vlastnosti služby SharePoint. Například namísto zadání konkrétního [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] řetězce pro web služby SharePoint můžete použít `$(SharePointSiteUrl)` .

> [!NOTE]
> [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]K určení vlastnosti můžete použít buď proměnnou syntaxe `$(` *PropertyName* , `)` nebo syntaxe proměnné prostředí `%` *PropertyName* `%` .

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)