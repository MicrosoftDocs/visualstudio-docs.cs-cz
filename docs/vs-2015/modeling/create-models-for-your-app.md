---
title: Vytváření modelů pro aplikaci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9f20629c39bc37ca20550c3b88d8ecb2aca470f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300255"
---
# <a name="create-models-for-your-app"></a>Vytváření modelů pro aplikaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagramy modelování vám pomůžou pochopit, objasnit a sdělovat nápady týkající se vašeho kódu a požadavky uživatelů, které musí váš softwarový systém podporovat. Pokud například chcete popsat a sdělit požadavky uživatelů, můžete použít jazyk UML (Unified Modeling Language) (UML) použití, činnosti, třídy a sekvenční diagramy. Chcete-li popsat a sdělit funkce systému, můžete použít diagramy komponent, tříd, aktivit a sekvenčních UML.

 Viz [video o kanálu 9: vylepšení architektury prostřednictvím modelování](https://go.microsoft.com/fwlink/?LinkID=252078).

 V této verzi můžete vytvořit následující diagramy UML:

|**Znázorňuje**|**Objeví**|
|-----------------|---------------|
|[Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)|Tok práce mezi akcemi a účastníky v obchodním procesu|
|[Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)|Součásti systému, jejich rozhraní, porty a vztahy|
|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|Typy, které se používají k ukládání a výměně dat v systému a jejich vztazích|
|[Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)|Sekvence interakcí mezi objekty, komponentami, systémy nebo aktéry|
|[Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)|Uživatelské cíle a úkoly, které systém podporuje|

 Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé typy diagramů, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 K vizualizaci architektury systému nebo existujícího kódu vytvořte následující diagramy:

|**Znázorňuje**|**Objeví**|
|-----------------|---------------|
|[Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)|Architektura vysoké úrovně systému|
|Mapy kódu<br /><br /> [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)|Závislosti a další vztahy v existujícím kódu|
|Diagramy tříd generovaných kódem<br /><br /> [Práce s diagramy tříd (Návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md)|Typy a jejich vztahy v kódu .NET|

## <a name="common-tasks"></a>Obecné úlohy

|**Téma**|**Úloha**|
|---------------|--------------|
|[Vytváření projektů a diagramů pomocí modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Vytvářejte modely** a přidejte diagramy.|
|[Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)|**Nakreslete diagramy** pro úpravu modelu.|
|[Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md)|**Vytvořte balíčky** pro rozdělení modelu na jednotky, na kterých mohou pracovat různí členové týmu.|
|[Generování kódu z diagramů tříd UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Vygenerujte C# kód z diagramů tříd** pro zahájení implementace.|
|[Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Přizpůsobení prvků modelu** pomocí stereotypů pro účely rozšiřování standardních prvků modelu UML pro konkrétní účely.|
|[Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)|**Vytvořte propojení mezi prvky modelu a pracovními položkami** , které vám pomohou sledovat úkoly, testovací případy, chyby, požadavky, problémy nebo jiné druhy práce, které jsou spojeny s konkrétními částmi modelu.|
|[Exportování diagramů jako obrázků](../modeling/export-diagrams-as-images.md)|**Uložte model a diagramy** , abyste je mohli sdílet s ostatními uživateli, včetně těch, kteří nepoužívají [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|

## <a name="related-tasks"></a>Související úlohy

|**Téma**|**Úloha**|
|---------------|--------------|
|[Vizualizace kódu](../modeling/visualize-code.md)|Vytvářejte mapy kódu a diagramy vrstev pro lepší pochopení neznámého kódu.|
|[Modelování uživatelských požadavků](../modeling/model-user-requirements.md)|Použijte modely k objasnění potřeb uživatelů a jejich sdělování.|
|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|Použijte modely k popisu celkové struktury a chování systému a ujistěte se, že vyhovují potřebám uživatelů.|
|[Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)|Ujistěte se, že váš software zůstává v souladu s požadavky vašich uživatelů a celkovou architekturou systému.|
|[Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)<br /><br /> [Používání modelů v agilním vývoji](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Použijte modely, které vám pomůžou pochopit a změnit svůj systém během vývoje.|
|[Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)|Uspořádejte modely ve velkém nebo středním projektu.|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|------------------|---------------|
|**Fóra**|-   [nástrojů pro modelování sady Visual Studio pro vizualizaci &](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
