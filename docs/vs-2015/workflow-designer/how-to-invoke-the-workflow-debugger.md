---
title: 'Postupy: vyvolání ladicího programu pracovního postupu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 34c5cdae4b8730c9058a87061456d5ab6d186c53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603672"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Postupy: vyvolání ladicího programu pracovního postupu
Obecně je potřeba ladit pracovní postupy stejně jako při ladění programů napsaných v jiných programovacích jazycích sady Visual Studio. Ladicí program pracovního postupu můžete spustit následujícími způsoby:

- V nabídce **ladění** vyberte **připojit k procesu** a vyberte běžící hostitelský proces pro vaši instanci pracovního postupu. Tento postup je stejný jako připojení k hostitelskému procesu ve spravovaném kódu.

- Stiskněte klávesu **F5** ke spuštění instance pracovního postupu nebo ke spuštění i po dosažení zarážky.

- Použijte vzdálené ladění. Informace o použití vzdáleného ladění naleznete v tématu [How to: Enable Remote Debugging](http://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Pokud se aplikace pracovního postupu zaměřuje na architekturu x86 a je hostovaná na počítači, na kterém běží operační systém 64, pak vzdálené ladění nebude fungovat, pokud se na vzdáleném počítači nenainstaluje [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] nebo když se cíl pro aplikaci pracovního postupu změní na  **Libovolný procesor**.

### <a name="stepping-through-code"></a>Krokování prostřednictvím kódu

- **Krok**dovnitř: můžete krokovat s aktivitou pomocí **klávesy F11**. Ladicí program popisuje všechny definované obslužné rutiny. Pokud není definována žádná obslužná rutina, můžete krokovat s aktivitou nebo se složenými aktivitami, které obsahují další aktivity, a krokovat s první vykonávanou aktivitou.

- **Krok ven:** Můžete krokovat s aktivitou pomocí **SHIFT + F11**. Krokování mimo aktivitu spustí aktuální aktivitu a všechny její aktivity na stejné úrovni jako dokončené. Ladicí program se pak rozdělí na nadřazený objekt aktuální aktivity. Při rozkrokování z obslužné rutiny kódu se ladicí program ukončí u aktivity, ke které je přidružena obslužná rutina.

- **Krok za krokem**: můžete krokovat aktivitu pomocí **F10**. Při krokování nad složenou aktivitou se ladicí program ukončí u prvního spustitelného prvku složené aktivity. Při rozkrokování mimo nesložené, například <xref:System.Activities.Statements.Assign> aktivity, ladicí program spustí aktivitu a její přidružené obslužné rutiny a přeruší na další aktivitu. Pokud je spuštěná aktivita poslední podřízená aktivita v složené aktivitě, potom po provedení dojde k přerušení ladicího programu u nadřazené aktivity.

### <a name="debugging-with-f5"></a>Ladění pomocí F5

- Pokud vytváříte projekt konzolové aplikace pracovního postupu, stačí stisknout klávesu **F5** a zahájit tak ladění aplikace a pracovního postupu. Pokud vytváříte knihovnu aktivit sami, musíte mít spustitelnou aplikaci hostitele jako projekt po spuštění. Chcete-li nastavit projekt po spuštění v **Průzkumník řešení**, klikněte pravým tlačítkem myši na název projektu hostitele a vyberte **nastavit jako spouštěný projekt**.

## <a name="see-also"></a>Viz také
 [Postupy: nastavení zarážek v pracovních](../workflow-designer/how-to-set-breakpoints-in-workflows.md) postupech [ladění pracovních postupů pomocí Návrhář postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)