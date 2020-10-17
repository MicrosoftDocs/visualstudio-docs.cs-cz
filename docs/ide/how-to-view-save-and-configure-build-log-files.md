---
title: 'Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení | Microsoft Docs'
description: Přečtěte si, jak můžete zobrazit, Uložit a nakonfigurovat soubory protokolu sestavení. Tyto soubory poskytují užitečné informace pro úlohy, jako je řešení potíží při selhání sestavení.
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02d26416357ec13b61232f2adb0bc3e5e3c67818
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136599"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení

Po sestavení projektu v integrovaném vývojovém prostředí sady Visual Studio můžete zobrazit informace o tomto sestavení v okně **výstup** . Pomocí těchto informací můžete například řešit potíže při selhání sestavení.

- V případě projektů v jazyce C++ lze také zobrazit stejné informace v souboru protokolu, který je vytvořen a uložen při sestavení projektu. 

- Pro projekty spravovaného kódu můžete kliknout na okno výstup sestavení a stisknout **kombinaci kláves CTRL +** + **S**. Visual Studio vás vyzve k zadání umístění pro uložení informací z okna **výstup** do souboru protokolu.

Rozhraní IDE lze také použít k určení, jaké druhy informací chcete zobrazit o jednotlivých sestaveních.

Pokud sestavíte jakýkoli typ projektu pomocí nástroje MSBuild, můžete vytvořit soubor protokolu pro uložení informací o sestavení. Další informace najdete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Zobrazení souboru protokolu sestavení pro projekt C++

1. V **Průzkumníku Windows** nebo **Průzkumníkovi souborů**otevřete následující soubor (relativní vzhledem k kořenové složce projektu): *release* \\ <ProjectName> \> . Log * nebo *Debug \\<ProjectName \> . log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Vytvoření souboru protokolu sestavení pro projekt spravovaného kódu

1. Na řádku nabídek klikněte na **sestavit**sestavení  >  **řešení**.

2. V okně **výstup** klikněte někam do textu.

3. Stiskněte klávesy **CTRL** + **S**.

   Visual Studio vás vyzve k zadání umístění pro uložení výstupu sestavení.

Můžete také vygenerovat protokoly spuštěním nástroje MSBuild přímo z příkazového řádku pomocí `-fileLogger` `-fl` Možnosti příkazového řádku (). Viz [získání protokolů sestavení pomocí nástroje MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Změna množství informací obsažených v protokolu sestavení

1. Na panelu nabídek vyberte **Tools**  >  **Možnosti**nástroje.

2. Na stránce **projekty a řešení** vyberte stránku **sestavení a spuštění** .

3. V seznamu **podrobností výstupu sestavení projektu nástroje MSBuild** zvolte jednu z následujících hodnot a pak klikněte na tlačítko **OK** .

    |Úroveň podrobností|Popis|
    | - |-----------------|
    |**Quiet**|Zobrazí souhrn pouze pro sestavení.|
    |**Minimální**|Zobrazí souhrn sestavení a chyb, upozornění a zpráv, které jsou zařazeny do kategorie s vysokou důležitostí.|
    |**Normální**|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou zařazeny do kategorie jako vysoce důležité; a hlavní kroky sestavení. Tuto úroveň podrobností budete používat častěji.|
    |**Detailed**|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou zařazeny do kategorie jako vysoce důležité; všechny kroky sestavení; zprávy, které jsou zařazeny do kategorií normálním významem.|
    |**diagnostické**|Zobrazí všechna data, která jsou k dispozici pro sestavení. Tuto úroveň podrobností můžete použít k usnadnění ladění problémů s vlastními skripty sestavení a dalšími problémy s sestavením.|

     Další informace najdete v [dialogovém okně Možnosti, projekty a řešení, sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) a <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Je nutné znovu sestavit projekt, aby se změny projevily v okně **výstup** (všechny projekty) a souboru * \<ProjectName> . txt* (pouze projekty C++).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Použití binárních protokolů pro snazší procházení velkých souborů protokolu

Binární protokoly jsou volitelnou funkcí pro projekty .NET, které vám umožní získat bohatší možnosti procházení protokolů, které by mohly usnadnit hledání informací ve velkých protokolech. Chcete-li použít binární protokoly, nainstalujte [Systémové nástroje projektu](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Další informace najdete v tématu [https://msbuildlog.com](https://msbuildlog.com) a v [binárním protokolu](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md) .

## <a name="see-also"></a>Viz také

- [Sestavování a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
