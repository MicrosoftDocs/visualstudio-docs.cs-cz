---
title: 'Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 26ece0c0d46e5c747ac05bae8c2d4fc793c34601
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207399"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Postupy: Zobrazování, ukládání a konfigurace souborů protokolu sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po sestavení projektu v integrovaném vývojovém prostředí sady Visual Studio můžete zobrazit informace o daném sestavení ve **výstup** okna. Pomocí těchto informací je možné, třeba řešit selhání sestavení. Pro projekty C++ můžete také zobrazit tyto informace v souboru .txt, který má vytvořili a uložili automaticky. Pro projekty spravovaného kódu, můžete kopírovat a vkládat informace z **výstup** okno TXT soubor a uložte ho sami. Můžete také integrovaného vývojového prostředí k určení, jaké typy informací, které chcete zobrazit informace o každém sestavení.  
  
 Pokud vytváříte jakýkoli druh projektu pomocí nástroje MSBuild, můžete vytvořit soubor .txt, chcete-li uložit informace o sestavení. Další informace najdete v tématu [získávání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### <a name="to-view-the-build-log-file-for-a-c-project"></a>Chcete-li zobrazit soubor protokolu sestavení pro projekt jazyka C++  
  
1.  V **Windows Explorer** nebo **Průzkumníka souborů**, otevřete následující soubor: \\...\Visual Studio *verze*\Projects\\  *ProjectName*\\*ProjectName*\Debug\\*ProjectName*txt  
  
### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Chcete-li vytvořit soubor protokolu sestavení pro projekt spravovaného kódu  
  
1.  V panelu nabídky zvolte **sestavení**, **sestavit řešení**.  
  
2.  V **výstup** okně měli na očích informace ze sestavení a potom ho zkopírujte do schránky.  
  
3.  Otevřete textový editor, jako je například Poznámkový blok, vložte informace do souboru a pak ho uložte.  
  
### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Chcete-li změnit množství informací o zahrnutých do protokolu sestavení  
  
1.  V panelu nabídky zvolte **nástroje**, **možnosti**.  
  
2.  Na **projekty a řešení** zvolte **sestavíte a spustíte** stránky.  
  
3.  V **podrobnosti výstupu sestavení projektu nástroje MSBuild** seznamu, vyberte jednu z následujících hodnot a klikněte na tlačítko **OK** tlačítko.  
  
    |Úroveň podrobností|Popis|  
    |---------------------|-----------------|  
    |Quiet|Zobrazí souhrn pouze sestavení.|  
    |Minimální|Zobrazí souhrn sestavení a chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité.|  
    |Normální|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité. a hlavní kroky sestavení. Tato úroveň podrobností budete používat nejčastěji.|  
    |Podrobné|Zobrazí souhrn sestavení; chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité. všechny kroky sestavení; a zprávy, které jsou klasifikovány od normální význam.|  
    |Diagnostika|Zobrazí všechna data, která je k dispozici pro sestavení. Tato úroveň podrobností můžete použít k ladění problémů s skripty vlastního sestavení a další problémy se sestavením.|  
  
     Další informace najdete v tématu [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) a <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  Je nutné znovu sestavit projekt pro vaše změny se projeví **výstup** okno (všechny projekty) a *ProjectName*souboru .txt (pouze C++ projektů).  
  
## <a name="see-also"></a>Viz také  
 [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Sestavování a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)



