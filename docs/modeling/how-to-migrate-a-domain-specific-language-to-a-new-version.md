---
title: 'Postupy: Migrace projektu Domain-Specific Language'
description: Tento článek obsahuje informace o tom, jak migrovat projekt jazyka specifický pro doménu na novější verzi Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8119f465e32d3754dc446524286e0a2c12dedc40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387187"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Postupy: Migrace jazyka specifického pro doménu na novou verzi
Projekty, které definují a používají jazyk specifický pro doménu, můžete migrovat z verze nástroje , [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] která byla distribuována pomocí nástroje [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Nástroj pro migraci je součástí nástroje [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . Nástroj převede všechny Visual Studio a řešení, která používají nebo definují nástroje DSL.

 Nástroj pro migraci musíte spustit explicitně: nespuštěný automaticky při otevření řešení v Visual Studio. Tento nástroj a podrobný dokument s pokyny najdete v této cestě:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Před migrací projektů DSL
 Nástroj pro migraci upraví Visual Studio souborů projektu (**.csproj**) a souborů řešení (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Příprava projektů na migraci

- Ujistěte se, že je možné zapisovat soubory **.csproj** a **.sln.** Pokud jsou ve zdrojovém kódu, ujistěte se, že jsou rezervovány.

- Vytvořte kopii složek, které chcete migrovat.

## <a name="migrating-a-collection-of-projects"></a>Migrace kolekce projektů

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Migrace projektů a řešení DSL do Visual Studio 2010

1. Spusťte nástroj pro migraci DSL.

   - Můžete dvakrát kliknout na nástroj v Průzkumník Windows (nebo Průzkumník souborů) nebo spustit nástroj z příkazového řádku. Nástroj se nachází v tomto umístění:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Zvolte složku obsahující řešení a projekty, které chcete převést.

   - Do pole v horní části nástroje zadejte cestu nebo klikněte na **Procházet.**

     Nástroj pro migraci zobrazí strom projektů, které definují nebo používají seznamy DSL. Strom obsahuje každý projekt, který používá **sestavení Microsoft.VisualStudio.Modeling.Sdk** nebo **TextTemplating.**

3. Zkontrolujte strom projektů a zrušte zaškrtnutí projektů, které nechcete převést.

   - Výběrem projektu nebo řešení zobrazíte seznam změn, které nástroj změní.

       > [!NOTE]
       > Zaškrtávací políčka zobrazená vedle názvů složek nemají žádný vliv. Abyste si projekty a řešení prošetřili, musíte složky rozbalit.

4. Převeďte projekty.

   1. Klikněte na tlačítko **Převést**.

        Před převodem každého souboru projektu se uloží kopie **projektu .csproj** jako **projekt .vs2008.csproj.**

        Kopie **.sln každého řešení** se uloží _jako_**řešení .vs2008.sln.**

   2. Prozkoumejte všechny neúspěšné převody, které jsou hlášeny.

        Chyby se hlásí v textovém okně. Kromě toho stromové zobrazení zobrazuje červený příznak na každém uzlu, který se nepodařilo převést. Kliknutím na uzel můžete získat další informace o této chybě.

5. **Transformovat všechny šablony** v řešeních obsahujících úspěšně převedené projekty.

   1. Otevřete řešení.

   2. Klikněte na **tlačítko Transformovat všechny** šablony v záhlaví Průzkumník řešení.

       > [!NOTE]
       > Tento krok můžete zbytečovat. Další informace najdete v tématu [Automatizace transformace všech šablon.](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

6. Aktualizujte vlastní kód v převedených projektech.

   - Pokuste se sestavit projekty a prošetřovat případná selhání.

   - Otestujte návrháře.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Viz také

- [Související blogové příspěvky](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)