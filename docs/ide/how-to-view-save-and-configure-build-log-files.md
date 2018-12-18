---
title: 'Postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení | Dokumentace Microsoftu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b745a9e74fd4016db60883b06091a33c6d30d52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860666"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení

Po sestavení projektu v integrovaném vývojovém prostředí sady Visual Studio můžete zobrazit informace o daném sestavení ve **výstup** okna. Pomocí těchto informací je možné, třeba řešit selhání sestavení. Pro projekty C++, můžete také zobrazit stejné informace *.txt* soubor, který má vytvořili a uložili automaticky. Pro projekty spravovaného kódu, můžete kopírovat a vkládat informace z **výstup** okno do *.txt* soubor a uložte ho sami. Můžete také integrovaného vývojového prostředí k určení, jaké typy informací, které chcete zobrazit informace o každém sestavení.

Pokud vytvoříte pomocí nástroje MSBuild jakýkoli druh projektu, můžete vytvořit *.txt* soubor se uloží informace o sestavení. Další informace najdete v tématu [získat protokoly o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Chcete-li zobrazit soubor protokolu sestavení pro projekt jazyka C++

1.  V **Windows Explorer** nebo **Průzkumníka souborů**, otevřete následující soubor:  *\\...\Visual Studio \<verze\>\Projects\\ < ProjectName\>\\< ProjectName\>\Debug\\< ProjectName\>txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Chcete-li vytvořit soubor protokolu sestavení pro projekt spravovaného kódu

1.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.

2.  V **výstup** okně měli na očích informace ze sestavení a potom ho zkopírujete do **schránky**.

3.  Otevřete textový editor, například **Poznámkový blok**, vložte informace do souboru a pak ho uložte.

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Chcete-li změnit množství informací o zahrnutých do protokolu sestavení

1.  V panelu nabídky zvolte **nástroje** > **možnosti**.

2.  Na **projekty a řešení** zvolte **sestavíte a spustíte** stránky.

3.  V **podrobnosti výstupu sestavení projektu nástroje MSBuild** seznamu, vyberte jednu z následujících hodnot a klikněte na tlačítko **OK** tlačítko.

    |Úroveň podrobností|Popis|
    | - |-----------------|
    |**Nastaví tichý**|Zobrazí souhrn pouze sestavení.|
    |**Minimální**|Zobrazí souhrn sestavení a chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité.|
    |**Normální**|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité. a hlavní kroky sestavení. Tato úroveň podrobností budete používat nejčastěji.|
    |**Podrobné**|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité. všechny kroky sestavení; a zprávy, které jsou klasifikovány od normální význam.|
    |**Diagnostika**|Zobrazí všechna data, která je k dispozici pro sestavení. Tato úroveň podrobností můžete použít k ladění problémů s skripty vlastního sestavení a další problémy se sestavením.|

     Další informace najdete v tématu [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) a <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Je nutné znovu sestavit projekt pro vaše změny se projeví **výstup** okno (všechny projekty) a  *<ProjectName>.txt* souboru (pouze C++ projekty).

## <a name="see-also"></a>Viz také:

- [Získání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Sestavení a vyčištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)