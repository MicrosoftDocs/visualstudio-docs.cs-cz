---
title: 'Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení | Dokumenty společnosti Microsoft'
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84efda930066c4236fa4397fbadf287c6774fdb0
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472790"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení

Po sestavení projektu v ide sady Visual Studio, můžete zobrazit informace o tomto sestavení v okně **Výstup.** Pomocí těchto informací můžete například řešit selhání sestavení.

- U projektů jazyka C++ můžete také zobrazit stejné informace v souboru protokolu, který je vytvořen a uložen při vytváření projektu. 

- U projektů spravovaného kódu můžete klepnout do okna výstupu sestavení a stisknout **kombinaci kláves Ctrl**+**S**. Visual Studio vás vyzve k umístění pro uložení informací z okna **Výstup** do souboru protokolu.

Pomocí ide můžete také určit, jaké druhy informací, které chcete zobrazit o každé sestavení.

Pokud vytvoříte jakýkoli druh projektu pomocí MSBuild, můžete vytvořit soubor protokolu pro uložení informací o sestavení. Další informace naleznete v [tématu Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Zobrazení souboru protokolu sestavení pro projekt jazyka C++

1. V **Průzkumníkovi Windows** nebo **Průzkumníkovi souborů**otevřete následující soubor (vzhledem k kořenové složce projektu): *Vydání*\\<ProjectName>\>. Protokol* nebo *Ladění\\<\>název_aplikace .log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Vytvoření souboru protokolu sestavení pro projekt spravovaného kódu

1. Na řádku nabídek zvolte **Build** > **Build Build Solution**.

2. V okně **Výstup** klikněte někde v textu.

3. Stiskněte **klávesu Ctrl**+**S**.

   Visual Studio vás vyzve k umístění k uložení výstupu sestavení.

Protokoly můžete také generovat spuštěním msbuildu přímo `-fileLogger` z`-fl`příkazového řádku pomocí možnosti příkazového řádku ( ). Viz [Získání protokolů sestavení pomocí msbuild .](../msbuild/obtaining-build-logs-with-msbuild.md)

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Změna množství informací zahrnutých do protokolu sestavení

1. Na řádku nabídek zvolte**Možnosti** **nástrojů** > .

2. Na stránce **Projekty a řešení** zvolte stránku **Sestavení a spuštění.**

3. V seznamu **podrobností o vytváření sestavení projektu MSBuild** zvolte jednu z následujících hodnot a pak zvolte tlačítko **OK.**

    |Úroveň podrobností|Popis|
    | - |-----------------|
    |**Tichý**|Zobrazí pouze souhrn sestavení.|
    |**Minimální**|Zobrazí souhrn sestavení a chyby, upozornění a zprávy, které jsou kategorizovány jako velmi důležité.|
    |**Normální**|Zobrazí souhrn sestavení; chyby, upozornění a zprávy, které jsou klasifikovány jako velmi důležité; a hlavní kroky sestavení. Budete používat tuto úroveň podrobností nejčastěji.|
    |**Detailed**|Zobrazí souhrn sestavení; chyby, upozornění a zprávy, které jsou klasifikovány jako velmi důležité; všechny kroky sestavení; a zprávy, které jsou rozděleny do kategorií podle normálnídůležitosti.|
    |**Diagnostické**|Zobrazí všechna data, která jsou k dispozici pro sestavení. Tuto úroveň podrobností můžete použít k ladění problémů s vlastní mise skripty sestavení a další problémy sestavení.|

     Další informace naleznete v [tématu Dialogové okno Možnosti, Projekty a řešení, Sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) a <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Změny se projeví v okně **Výstup** (všechny projekty) a v souboru * \<ProjectName>.txt* (pouze projekty jazyka C++).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Použití binárních protokolů k usnadnění procházení velkých souborů protokolu

Binární protokoly jsou volitelnou funkcí pro projekty .NET, která umožňuje mít bohatší procházení protokolu, které mohou usnadnit hledání informací ve velkých protokolech. Chcete-li použít binární protokoly, nainstalujte [systémové nástroje projektu](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Další informace naleznete [https://msbuildlog.com](https://msbuildlog.com) v tématech a [binárních protokolech](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Viz také

- [Vytváření a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
