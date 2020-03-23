---
title: Přehled jazykových nástrojů specifických pro doménu | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652150"
---
# <a name="overview-of-domain-specific-language-tools"></a>Přehled Jazykových nástrojů specifických pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje jazyka specifické pro doménu (Nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]DSL), které jsou hostovány v aplikaci , umožňují navrhnout jazyk specifický pro doménu a poté generovat vše, co uživatelé musí mít k vytvoření modelů založených na jazyce.

 Následující nástroje jsou součástí nástroje DSL:

- Průvodce projektem, který používá různé šablony řešení, které vám pomohou začít vyvíjet jazyk specifický pro doménu.

- Grafický návrhář pro vytváření a úpravy definice jazyka specifické ho za doménu.

- Ověřovací modul, který zajišťuje, že definice jazyka specifické pro doménu je ve správném formátu a zobrazí chyby a upozornění, pokud existují problémy.

- Generátor kódu, který bere definici jazyka specifické pro doménu jako vstup a vytváří zdrojový kód jako výstup.

## <a name="the-dsl-tools-solution"></a>Řešení nástrojů DSL
 Průvodce návrhářem specifickým pro doménu poskytuje následující šablony řešení:

- Tok úkolů

- Diagramy tříd

- Minimální jazyk

- Modely komponent

- Minimální WPF

- Minimální Windows.Forms

- Knihovna DSL

  Další informace naleznete [v tématu Výběr šablony jazykového řešení specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Průvodce vytvoří [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které má následující projekty:

- Dsl

   Dsl projekt definuje jazyk specifický pro doménu a jeho nástroje pro úpravy a zpracování.

- **Balíček DslPackage**

   Projekt DslPackage určuje, jak se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]jazykové nástroje integrují s .

## <a name="the-dsl-tools-graphical-interface"></a>Grafické rozhraní nástroje DSL
 Grafické rozhraní Nástroje DSL můžete použít k přidání prvků a vztahů do jazyka specifického pro doménu. Po přidání prvků můžete definovat jejich vzhled jejich mapováním na obrazce, přizpůsobením barev a přidáním dekoratérů. Prvky můžete také přidat do panelu nástrojů.

## <a name="validation-in-dsl-tools"></a>Ověření v nástrojích DSL
 Dsl poskytuje jednu úroveň ověření a ujistěte se, že model domény splňuje základní požadavky pro generování kódu. Obvykle při vytváření vlastního jazyka specifického pro doménu byste přidat vlastní ověření vyjádřit pravidla obchodní logiky. Další informace o vlastním ověření naleznete [v tématu Ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).

 Doporučujeme, abyste při navrhování jazyku specifického pro doménu často ověřovali jazyk specifický pro doménu. Pokud jazyk specifický pro doménu má chyby ověření, nelze generovat zdrojový kód. Proces generování zdrojového kódu ze šablon se provádí klepnutím na **tlačítko Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení. Při každé úpravě definice jazyka se také ujistěte, že **transformujete všechny šablony**. Další informace naleznete v [tématu How to: Create a Domain-Specific Language Solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Přizpůsobení nástrojů DSL
 Můžete poskytnout další kód pro upřesnění chování modelu a definovat omezení nad jazykem. V případě potřeby můžete provést významné změny úpravou textových šablon.

## <a name="distributing-your-dsl-solution"></a>Distribuce řešení DSL
 Nástroje DSL generuje balíček, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]je hostován v . Balíček zobrazuje panel nástrojů, průzkumník DSL a další prvky uživatelského rozhraní, které umožňují uživatelům vytvářet modely pomocí jazyka specifického pro doménu.

 Při vytváření a spuštění řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]DSL Tools v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplikaci , druhá instance ukazuje, jak váš jazyk specifický pro doménu vypadá pro uživatele jazyka. Po ověření, že vše funguje správně, můžete distribuovat `.vsix` soubor, který najdete ve složce sestavení projektu DslPackage. Tento soubor lze nainstalovat DSL jako [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příponu v jiných počítačích.  Další informace naleznete v [tématu Nasazení jazykových řešení specifických pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také
 [The Experimental Instance](../extensibility/the-experimental-instance.md) [Glosář jazykových nástrojů specifických pro experimentální instance](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
