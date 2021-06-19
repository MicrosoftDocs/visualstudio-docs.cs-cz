---
title: Přehled Jazykových nástrojů specifických pro doménu
description: Zjistěte, jak nástroje DSL umožňují navrhovat jazyk specifický pro doménu a pak vygenerovat vše, co uživatelé musí mít k vytváření modelů založených na tomto jazyce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 004c9929b33878359fa23735189d60939953755a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390903"
---
# <a name="overview-of-domain-specific-language-tools"></a>Přehled Jazykových nástrojů specifických pro doménu
Domain-Specific Language Tools (nástroje DSL), které jsou hostované v Visual Studio, vám umožňují navrhnout jazyk specifický pro doménu a pak vygenerovat vše, co uživatelé musí mít k vytváření modelů založených na jazyce.

 V nástrojích DSL jsou zahrnuté následující nástroje:

- Průvodce projektem, který používá různé šablony řešení, vám pomůže začít s vývojem jazyka specifického pro doménu.

- Grafický návrhář pro vytváření a úpravy definice jazyka specifické pro doménu.

- Ověřovací modul, který zajišťuje, aby definice jazyka specifická pro doménu byla ve správném formátu, a v případě problémů zobrazuje chyby a upozornění.

- Generátor kódu, který jako vstup přebírá definici jazyka specifickou pro doménu a jako výstup vytváří zdrojový kód.

## <a name="the-dsl-tools-solution"></a>Řešení DSL Tools
 Průvodce Domain-Specific Návrhářem nabízí následující šablony řešení:

- Tok úloh

- Diagramy tříd

- Minimální jazyk

- Modely komponent

- Minimální WPF

- Minimální Windows.Forms

- Knihovna DSL

  Další informace najdete v tématu [Výběr šablony Domain-Specific jazyka](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Průvodce vytvoří nové Visual Studio, které má následující projekty:

- Dsl

   Projekt Dsl definuje jazyk specifický pro doménu a jeho nástroje pro úpravy a zpracování.

- **DslPackage**

   Projekt DslPackage určuje, jak se nástroje jazyka integrují s Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Grafické rozhraní nástrojů DSL
 Grafické rozhraní DSL Tools můžete použít k přidání prvků a relací do jazyka specifického pro doménu. Po přidání prvků můžete definovat jejich vzhled jejich mapováním na tvary, přizpůsobením barev a přidáním dekorátorů. Prvky můžete také přidat do sady nástrojů.

## <a name="validation-in-dsl-tools"></a>Ověřování v nástrojích DSL
 Dsl poskytuje jednu úroveň ověřování, aby se ujistil, že doménový model splňuje základní požadavky na generování kódu. Při vytváření vlastního jazyka specifického pro doménu byste obvykle k vyjádření pravidel obchodní logiky měli přidat vlastní ověřování. Další informace o vlastním ověřování najdete v tématu [Ověřování v jazyce Domain-Specific.](../modeling/validation-in-a-domain-specific-language.md)

 Doporučujeme, abyste při návrhu často ověřovat jazyk specifický pro doménu. Pokud v jazyce specifickém pro doménu dochází k chybám ověřování, nemůžete vygenerovat zdrojový kód. Proces generování zdrojového kódu ze šablon se provádí kliknutím na **Transformovat všechny** šablony na panelu nástrojů Průzkumník řešení. Vždy, když upravíte definici jazyka, nezapomeňte **také transformovat všechny šablony**. Další informace najdete v [tématu Postupy: Vytvoření řešení Domain-Specific Language.](../modeling/how-to-create-a-domain-specific-language-solution.md)

## <a name="customization-of-dsl-tools"></a>Přizpůsobení nástrojů DSL
 Můžete zadat další kód pro upřesnění chování modelu a definování omezení pro váš jazyk. V případě potřeby můžete provést významné změny úpravou textových šablon.

## <a name="distributing-your-dsl-solution"></a>Distribuce řešení DSL
 Nástroje DSL generují balíček, který je hostován v Visual Studio. Balíček zobrazí panel nástrojů, průzkumník DSL a další prvky uživatelského rozhraní, které uživatelům umožňují vytvářet modely pomocí jazyka specifického pro vaši doménu.

 Když sestavíte a spustíte řešení DSL Tools v Visual Studio, druhá instance Visual Studio vám ukáže, jak jazyk specifický pro doménu vypadá na uživatele jazyka. Po ověření, že vše funguje správně, můžete distribuovat soubor, který najdete ve složce `.vsix` sestavení projektu DslPackage. Tento soubor lze použít k instalaci DSL jako Visual Studio na jiných počítačích.  Další informace najdete v tématu [Nasazení Domain-Specific jazyka](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Viz také

- [Experimentální instance](../extensibility/the-experimental-instance.md)
- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))