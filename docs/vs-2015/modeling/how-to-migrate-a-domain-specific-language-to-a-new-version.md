---
title: 'Postupy: migrace jazyka specifického pro doménu na novou verzi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657332"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Postupy: Migrace jazyka specifického pro doménu na novou verzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete migrovat projekty, které definují a používají jazyk specifický pro doménu [!INCLUDE[vs2010](../includes/vs2010-md.md)] z verze [!INCLUDE[dsl](../includes/dsl-md.md)], která byla distribuována s [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 K dispozici je nástroj pro migraci, který je součástí [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]. Nástroj převádí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekty a řešení, která používají nebo definují nástroje DSL.

 Nástroj pro migraci musíte spustit explicitně: při otevření řešení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se nespustí automaticky. Nástroj a podrobný dokument s pokyny najdete v této cestě:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Před migrací projektů DSL
 Nástroj pro migraci upraví [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soubory projektu ( **. csproj**) a soubory řešení ( **. sln**).

#### <a name="to-prepare-projects-for-migration"></a>Příprava projektů pro migraci.

- Ujistěte se, že je možné zapsat soubory **. csproj** a **. sln** . Pokud se nacházejí pod správou zdrojových kódů, ujistěte se, že jsou rezervovány.

- Vytvořte kopii složek, které máte v úmyslu migrovat.

## <a name="migrating-a-collection-of-projects"></a>Migrace kolekce projektů

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Migrace projektů a řešení DSL do sady Visual Studio 2010

1. Spusťte nástroj pro migraci DSL.

   - Můžete dvakrát kliknout na nástroj v Průzkumníkovi Windows (nebo v Průzkumníku souborů) nebo spustit nástroj z příkazového řádku. Tento nástroj je v tomto umístění:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Vyberte složku, která obsahuje řešení a projekty, které chcete převést.

   - Zadejte cestu do pole v horní části nástroje nebo klikněte na tlačítko **Procházet**.

     Nástroj pro migraci zobrazuje strom projektů, které definují nebo používají DSL. Strom zahrnuje každý projekt, který používá sestavení **Microsoft. VisualStudio. Modeling. SDK** nebo **TextTemplating** .

3. Zkontrolujte strom projektů a zrušte kontrolu projektů, které nechcete převést.

   - Vyberte projekt nebo řešení, abyste zobrazili seznam změn, které nástroj provede.

       > [!NOTE]
       > Políčka, která se zobrazí vedle názvu složky, nemají žádný účinek. Aby bylo možné zkontrolovat projekty a řešení, je nutné rozbalit složky.

4. Převeďte projekty.

   1. Klikněte na tlačítko **převést**.

        Před převodem každého souboru projektu se uloží kopie _Project_ **. csproj** jako _Project_ **. vs2008. csproj.**

        Kopii každého _řešení_ **. sln** se uloží jako _Solution_ **. vs2008. sln.**

   2. Prozkoumejte všechny neúspěšné převody, které se nahlásily.

        Chyby jsou hlášeny v okně text. Stromové zobrazení navíc zobrazuje červený příznak na každém uzlu, který se nepovedlo převést. Kliknutím na uzel můžete získat další informace o tomto selhání.

5. **Transformuje všechny šablony** v řešení obsahujících úspěšně převedené projekty.

   1. Otevřete řešení.

   2. Klikněte na tlačítko **transformovat všechny šablony** v záhlaví Průzkumník řešení.

       > [!NOTE]
       > Tento krok je potřeba provést zbytečné. Další informace najdete v tématu [Jak automatizovat transformaci všech šablon](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6. Aktualizujte vlastní kód v převedených projektech.

   - Pokuste se sestavit projekty a prozkoumat případné chyby.

   - Otestujte návrháře.

## <a name="see-also"></a>Viz také
 [Co je nového ve vizualizaci a sadě SDK pro modelování](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
