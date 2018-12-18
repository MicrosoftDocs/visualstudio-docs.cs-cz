---
title: 'Postupy: vyvolání ladicího programu pracovních postupů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: acfbe34bc4a3d3c1139f8b1e821d9996fb8c712b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295734"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Postupy: vyvolání ladicího programu pracovních postupů
Obecně platí ladění pracovních postupů stejným způsobem, jako ladíte programy napsané v jiných programovacích jazycích sady Visual Studio. Ladicí program pracovního postupu můžete spustit následujícími způsoby:  
  
-   Vyberte **připojit k procesu** na **ladění** nabídky k výběru spuštěného hostitelský proces pro vaši instanci pracovního postupu. Tento postup je stejný jako připojení k procesu hostitele ve spravovaném kódu.  
  
-   Stisknutím klávesy **F5** spouštění instance pracovního postupu, nebo aby kontinuálně běžely, jakmile dosáhne zarážky.  
  
-   Použití vzdáleného ladění. Informace o použití vzdáleného ladění, naleznete v tématu [postupy: povolení vzdáleného ladění](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Pokud se aplikace pracovního postupu, zaměřuje x86 architektury a je hostovaná na počítači se systémem 64bitový operační systém, vzdálené ladění nebudou fungovat, pokud [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] je nainstalovaný na vzdáleném počítači nebo cíl pro aplikace pracovního postupu se změní na **Jakýkoli procesor**.  
  
### <a name="stepping-through-code"></a>Krokování kódem  
  
-   **Krok dovnitř**: můžete krokovat s vnořením aktivity pomocí **F11**. Ladicí program do libovolné obslužné rutiny, která je definována. Pokud není definována žádná obslužná rutina, Krokovat přes aktivity nebo pomocí složených aktivit, které obsahují další aktivity, přejdete na první spouštěné aktivity.  
  
-   **Krok Out:** můžete krokovat z aktivity pomocí **Shift-F11**. Krokování mimo aktivitu spouští aktuální aktivitu a jejich na stejné úrovni aktivity do konce. Ladicí program zastaví se na nadřazený prvek aktuální aktivity. Při procházení z obslužné rutiny kód, ladicí program přeruší na aktivitu, ke kterému je přidružené obslužnou rutinu.  
  
-   **Krokovat s přeskočením**: můžete krokovat přes aktivity pomocí **F10**. Při krokování přes složené aktivity, ladicí program přeruší na první spustitelný podřízený složené aktivity. Při krokování přes bez složeného, například <xref:System.Activities.Statements.Assign> aktivity, ladicí program provede aktivitu a jeho přidruženými obslužnými rutinami a zalomení na další aktivity. Pokud je aktivita, která se spustí poslední podřízenou aktivitou ve složených aktivit, pak po spuštění, ladicí program přeruší na Nadřazená aktivita.  
  
### <a name="debugging-with-f5"></a>Ladění pomocí F5  
  
-   Pokud vytváříte projekt konzolové aplikace pracovního postupu, stačí stisknout **F5** pro zahájení ladění do aplikace a pracovního postupu. Pokud vytváříte vlastní knihovny aktivit, musí mít aplikaci spustitelného souboru hostitele jako spouštěný projekt. Chcete-li nastavit projekt po spuštění **Průzkumníka řešení**, klikněte pravým tlačítkem na název hostitele a vyberte **nastavit jako spouštěný projekt**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavení zarážek v pracovních postupech](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Ladění pracovních postupů pomocí návrháře postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)