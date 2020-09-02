---
title: 'Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670498"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Postupy: Zobrazování, ukládání a konfigurace souborů protokolu sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po sestavení projektu v integrovaném vývojovém prostředí sady Visual Studio můžete zobrazit informace o tomto sestavení v okně **výstup** . Pomocí těchto informací můžete například řešit potíže při selhání sestavení. V případě projektů v jazyce C++ lze také zobrazit stejné informace v souboru. txt, který je vytvořen a uložen automaticky. Pro projekty spravovaného kódu můžete zkopírovat a vložit informace z okna **výstup** do souboru. txt a uložit je sami. Rozhraní IDE lze také použít k určení, jaké druhy informací chcete zobrazit o jednotlivých sestaveních.

 Pokud sestavíte jakýkoli typ projektu pomocí nástroje MSBuild, můžete vytvořit soubor. txt k uložení informací o sestavení. Další informace najdete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Zobrazení souboru protokolu sestavení pro projekt C++

1. V **Průzkumníku Windows** nebo **Průzkumníkovi souborů**otevřete následující soubor: \\ . ..\Visual Studio *verze*\Projects \\ *ProjectName* \\ *ProjectName*\debug. \\ *ProjectName*. txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Vytvoření souboru protokolu sestavení pro projekt spravovaného kódu

1. Na panelu nabídek vyberte **sestavení**, **řešení sestavení**.

2. V okně **výstup** zvýrazněte informace ze sestavení a pak ho zkopírujte do schránky.

3. Otevřete textový editor, například Poznámkový blok, vložte informace do souboru a pak ho uložte.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Změna množství informací obsažených v protokolu sestavení

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. Na stránce **projekty a řešení** vyberte stránku **sestavení a spuštění** .

3. V seznamu **podrobností výstupu sestavení projektu nástroje MSBuild** zvolte jednu z následujících hodnot a pak klikněte na tlačítko **OK** .

    |Úroveň podrobností|Popis|
    |---------------------|-----------------|
    |Quiet|Zobrazí souhrn pouze pro sestavení.|
    |Minimální|Zobrazí souhrn sestavení a chyb, upozornění a zpráv, které jsou zařazeny do kategorie s vysokou důležitostí.|
    |Normální|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou zařazeny do kategorie jako vysoce důležité; a hlavní kroky sestavení. Tuto úroveň podrobností budete používat častěji.|
    |Detailed|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou zařazeny do kategorie jako vysoce důležité; všechny kroky sestavení; zprávy, které jsou zařazeny do kategorií normálním významem.|
    |diagnostika|Zobrazí všechna data, která jsou k dispozici pro sestavení. Tuto úroveň podrobností můžete použít k usnadnění ladění problémů s vlastními skripty sestavení a dalšími problémy s sestavením.|

     Další informace najdete v [dialogovém okně Možnosti, projekty a řešení, sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) a <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Je nutné znovu sestavit projekt, aby se změny projevily v okně **výstup** (všechny projekty) a souboru *ProjectName*. txt (pouze projekty C++).

## <a name="see-also"></a>Viz také
 [Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) [vytváření a čištění projektů a řešení v prostředí Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [kompilace a sestavování](../ide/compiling-and-building-in-visual-studio.md)
