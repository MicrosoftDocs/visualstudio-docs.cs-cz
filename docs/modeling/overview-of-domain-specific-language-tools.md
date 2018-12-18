---
title: Přehled Jazykových nástrojů specifických pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 538ebb2121c488fa56f693a424f91b8af19a0c3e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966840"
---
# <a name="overview-of-domain-specific-language-tools"></a>Přehled Jazykových nástrojů specifických pro doménu
Nástroje jazyka specifického pro doménu (DSL Tools), které jsou hostovány v sadě Visual Studio, vám umožní navrhnout jazyka specifického pro doménu a potom generovat vše, co uživatelé musí mít k vytváření modelů, které jsou založeny na jazyce.

 Tyto nástroje jsou součástí nástroje DSL:

-   Průvodce projektem, který používá jiné řešení šablony můžete začít s vývojem jazyka specifického pro doménu.

-   Grafický návrhář pro vytváření a úpravu definice jazyka specifického pro doménu.

-   Modul ověřování, který zajišťuje, že definice jazyka specifického pro doménu ve správném formátu a pokud dojde k problémům se zobrazí chyby a upozornění.

-   Generátor kódu, který má definice jazyka specifického pro doménu jako vstup a vytvoří zdrojový kód jako výstup.

## <a name="the-dsl-tools-solution"></a>Řešení nástrojů DSL
 Průvodce Designer specifického pro doménu poskytuje následující šablony řešení:

- Tok úkolů

- Diagramy tříd

- Minimální jazykový

- Komponenta modelů

- Minimální WPF

- Minimální Windows.Forms

- Knihovna DSL, která

  Další informace najdete v tématu [výběr šablony řešení jazyka specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Průvodce vytvoří řešení sady Visual Studio, který má následující projekty:

- DSL

   Projektu Dsl definuje jazyka specifického pro doménu a jeho nástrojů úprav a zpracování.

- **DslPackage**

   DslPackage projektu určuje, jak integrovat nástroje jazyka pomocí sady Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Grafické rozhraní nástrojů DSL
 Přidání elementů a vztahů do jazyka specifického pro doménu, můžete použít grafické rozhraní nástrojů DSL. Po přidání prvků, můžete definovat jejich vzhled mapování na obrazce, přizpůsobení barev a přidáním dekorátory. Můžete také přidat prvky do panelu nástrojů.

## <a name="validation-in-dsl-tools"></a>Ověřování v nástroje DSL
 DSL poskytuje jednu úroveň ověření, že splňuje model domény základní požadavky pro generování kódu. Obvykle při vytváření jazyka specifického pro doménu přidáte vlastní ověření vyjádřit vaše obchodní logiky pravidla. Další informace o vlastních ověřovacích, naleznete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).

 Doporučujeme, abyste ověřili svůj jazyk specifický pro doménu často při jeho návrhu. Pokud doménově specifického jazyka došlo k chybám ověřování, nelze generovat zdrojový kód. Generování zdrojového kódu z šablon procesu se provádí kliknutím **Transformovat všechny šablony** na panelu nástrojů Průzkumníku řešení. Pokaždé, když změníte definice jazyka, nezapomeňte také **Transformovat všechny šablony**. Další informace najdete v tématu [postupy: vytváření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Přizpůsobení nástrojů DSL
 Můžete zadat další kód Upřesnit chování modelu a definování omezení přes svůj jazyk. V případě potřeby můžete provádět významné změny tak, že upravíte textových šablon.

## <a name="distributing-your-dsl-solution"></a>Distribuce řešení DSL
 Nástroje DSL vygeneruje balíček, který je hostovaný v sadě Visual Studio. Balíček se zobrazí panelu nástrojů Průzkumník DSL a další prvky uživatelského rozhraní, které umožní uživatelům vytvářet modely s využitím jazyka specifického pro doménu.

 Při sestavení a spuštění řešení nástrojů DSL v sadě Visual Studio, druhou instanci aplikace Visual Studio se dozvíte, jak vypadá jazyka specifického pro doménu pro uživatele jazyka. Až ověříte, že vše funguje správně, které můžete distribuovat `.vsix` soubor, který najdete ve složce sestavení testovaného projektu DslPackage. Tento soubor je možné nainstalovat DSL jako rozšíření sady Visual Studio v jiných počítačích.  Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také

- [Experimentální instance](../extensibility/the-experimental-instance.md)
- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)