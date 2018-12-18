---
title: 'Postupy: Migrace jazyka specifického pro doménu na novou verzi'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f736a8d5b8e09bbb1c5a894e3f0f450de19fd02f
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967022"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Postupy: Migrace jazyka specifického pro doménu na novou verzi
Můžete migrovat projekty, které definice a používání jazyka specifického pro doménu na [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] oproti verzi [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , který byl distribuován s [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Nástroj pro migraci se poskytuje jako součást [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Tento nástroj převede projektů sady Visual Studio a řešení, které používají nebo definovat nástroje DSL.

 Nástroj pro migraci musíte spustit explicitně: se nespustí automaticky při otevření řešení v sadě Visual Studio. Nástroje a dokument obsahuje podrobné pokyny najdete v této cestě:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Před migraci vašich projektů DSL
 Nástroj pro migraci upraví soubory projektu sady Visual Studio (**.csproj**) a soubory řešení (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Příprava migrace projektů.

-   Ujistěte se, **.csproj** a **.sln** lze zapisovat soubory. Pokud jsou pod správou zdrojových kódů, ujistěte se, že jsou rezervovány.

-   Vytvořte kopii složky, které máte v úmyslu migrovat.

## <a name="migrating-a-collection-of-projects"></a>Migrace kolekce projektů

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>K migraci DSL projekty a řešení pro Visual Studio 2010

1. Spusťte nástroj pro migraci DSL.

   -   Můžete dvakrát klikněte na panel nástrojů v Průzkumníku Windows (nebo Průzkumníka souborů) nebo spusťte nástroj z příkazového řádku. Tento nástroj je v tomto umístění:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Zvolte složku, která obsahuje řešení a projekty, které chcete převést.

   - Zadejte cestu do pole v horní části stránky nástroje, nebo klikněte na tlačítko **Procházet**.

     Nástroj pro migraci zobrazí strom projektů, které definují nebo použijte DSL. Každý projekt, který používá zahrnuje stromu **Microsoft.VisualStudio.Modeling.Sdk** nebo **TextTemplating** sestavení.

3. Kontrola stromu projektů a zrušte zaškrtnutí políčka projekty, které nechcete převést.

   -   Vyberte projekt nebo řešení zobrazíte seznam změn, které způsobí, že nástroj.

       > [!NOTE]
       >  Zaškrtávací políčka, které se zobrazují vedle názvu složky nemají žádný vliv. Je třeba rozbalit složky ke kontrole projekty a řešení.

4. Převod projektů.

   1.  Klikněte na tlačítko **převést**.

        Před každý soubor projektu je převést, kopie _projektu_**.csproj** budou uloženy jako _projektu_**. vs2008.csproj**

        Kopírování jednotlivých _řešení_**.sln** budou uloženy jako _řešení_**. vs2008.sln**

   2.  Prozkoumejte všechny neúspěšné převody, které jsou hlášeny.

        V textovém okně jsou hlášeny chyby. Kromě toho stromové zobrazení ukazuje rvená vlaječka v každém uzlu, který se nepovedlo převést. Můžete kliknout na uzel, který má získat další informace o této chybě.

5. **Transformovat všechny šablony** v řešení obsahující úspěšně převeden projekty.

   1.  Otevřete řešení.

   2.  Klikněte na tlačítko **Transformovat všechny šablony** tlačítko v hlavičce Průzkumníku řešení.

       > [!NOTE]
       >  Tento krok můžete provést zbytečné. Další informace najdete v tématu [jak automatizovat Transformovat všechny šablony](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Aktualizujte váš vlastní kód v projektech převedený.

   -   Pokus o sestavení projektů a prozkoumejte všechny chyby.

   -   Otestujte návrháře.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Viz také

- [Související blogové příspěvky](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)