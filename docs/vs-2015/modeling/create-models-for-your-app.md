---
title: Vytváření modelů pro aplikaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9e3aa389441914121493148ecb8fa45b9f86beed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745129"
---
# <a name="create-models-for-your-app"></a>Vytváření modelů pro aplikaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagramy modelování vám pochopit, objasnit a sdělovat nápady týkající se kódu a požadavky uživatelů, které váš softwarový systém musí podporovat. K popisu a sdělovat požadavky uživatelů, můžete například použít případ použití jazyka UML (Unified Modeling), aktivita, třídy a sekvenční diagramy. K popsání a prezentování funkčnosti vašeho systému, můžete použít komponentu, třídy, aktivity a sekvenční diagramy UML.  
  
 Zobrazit [Video pro kanál 9: zlepšení architektury prostřednictvím modelování](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Následující diagramy UML lze vytvořit v této verzi:  
  
|**Diagram**|**Ukazuje**|  
|-----------------|---------------|  
|[Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)|Tok mezi akcemi a účastníků v procesu podnikání práce|  
|[Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)|Součásti systému, jejich rozhraní, porty a relace|  
|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|Typy, které se používají k ukládání a vyměňovat data v systému a jejich vztahů|  
|[Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)|Sekvence interakcí mezi objekty, komponenty, systémy nebo objektů actor|  
|[Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)|Uživatelské cíle a úlohy, které systém podporuje|  
  
 Které verze sady Visual Studio podporovat každý typ diagramu najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 K vizualizaci architektury systému nebo existující kód, vytvořte následující diagramy:  
  
|**Diagram**|**Ukazuje**|  
|-----------------|---------------|  
|[Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)|Základní architektura systému|  
|Mapy kódu<br /><br /> [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)|Závislosti a jiné vztahy v existujícím kódu|  
|Diagramy tříd generovaný kód<br /><br /> [Práce s diagramy tříd (Návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md)|Typy a jejich vztahy v kódu rozhraní .NET|  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|**Téma**|**Úloha**|  
|---------------|--------------|  
|[Vytváření projektů a diagramů pomocí modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Vytvářejte modely** a přidání diagramů.|  
|[Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)|**Kreslení diagramů** k úpravě modelu.|  
|[Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md)|**Vytváření balíčků** rozdělit do jednotky, které se různí členové týmu můžete pracovat v modelu.|  
|[Generování kódu z diagramů tříd UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Generování kódu jazyka C# z diagramů tříd** ke spuštění vaší implementace.|  
|[Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Přizpůsobení prvků modelu** pomocí Stereotypy, rozšířit standardní elementů modelu UML pro konkrétní účely.|  
|[Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)|**Vytvoření propojení mezi elementy modelu a pracovních položek** můžete sledovat úkoly, testovací případy, chyby, požadavky, problémy nebo jiné druhy práce, které jsou spojeny s konkrétní části vašeho modelu.|  
|[Exportování diagramů jako obrázků](../modeling/export-diagrams-as-images.md)|**Uložit modelu a diagramů** tak, aby můžete je sdílet s ostatními uživateli, včetně těch, kteří nepoužívají [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|  
  
## <a name="related-tasks"></a>Související úlohy  
  
|**Téma**|**Úloha**|  
|---------------|--------------|  
|[Vizualizace kódu](../modeling/visualize-code.md)|Vytváření map kódu a diagramy vrstev pro lepší pochopení neznámého kódu.|  
|[Modelování uživatelských požadavků](../modeling/model-user-requirements.md)|Použití modelů a komunikaci potřebám uživatelů.|  
|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|Použijte modely k popisu celkovou strukturu a chování vašeho systému a ujistěte se, že bude vyhovovat potřebám uživatelů.|  
|[Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)|Ujistěte se, že software zůstane konzistentní s požadavky uživatelů a architektury systému.|  
|[Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)<br /><br /> [Použití modelů v Agilním vývoji](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)|Použití modelů pro vám pomůže pochopit a změnit systému během vývoje.|  
|[Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)|Uspořádejte modely ve velkém nebo středním projektu.|  
  
## <a name="external-resources"></a>Externí zdroje  
  
|**Kategorie**|**Odkazy**|  
|------------------|---------------|  
|**Fóra**|-   [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|



