---
title: Ladění pracovních postupů pomocí návrháře postupu provádění
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 482e13a91513151d7c4595e0a622f223751ae553
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755311"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Ladění pracovních postupů pomocí návrháře pracovních postupů

**Návrhář postupu provádění** poskytuje možnost ladění pracovních postupů a vlastní aktivity. Proces a chování jsou podobná výchozí ladicího programu sady Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Vyvolání pracovního postupu ladicí program

Obecně platí při ladění pracovních postupů, stejně jako při ladění programy vytvořené v jiné sadě Visual Studio programovací jazyky. Ladicí program pracovního postupu můžete spustit těmito způsoby:

- Vyberte **připojit k procesu** na **ladění** nabídce vyberte běžící proces hostitele pro instanci pracovního postupu. Tento postup je stejný jako připojování k hostitelskému procesu ve spravovaném kódu.

- Stiskněte klávesu **F5** spustit instance pracovního postupu nebo chcete-li pokračovat, aby po zarážku narazil spustila.

- Použití vzdálené ladění. Informace o používání vzdálené ladění najdete v tématu [postupy: povolení vzdáleného ladění](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Pokud je pracovní postup aplikace určena x86 architektura a je hostovaná na počítači se systémem 64bitový operační systém, pak vzdálené ladění nebude fungovat, pokud je na vzdáleném počítači nainstalované sady Visual Studio nebo cíle pro aplikace pracovního postupu se změní na  **Všechny procesoru**.

## <a name="step-through-code"></a>Krok prostřednictvím kódu

- **Krok v**: krokování s vnořením aktivitu stisknutím **F11**. Ladicí program do jakékoli obslužná rutina, která je definována. Pokud je definována žádná obslužná rutina, krok přes aktivity nebo složený aktivitami, které obsahují další aktivity, krok do první provádění aktivity.

- **Krok na více systémů:** vystoupení ze aktivitu stisknutím **Shift**+**F11**. Krokování s mimo aktivitu spouští aktuální aktivita a její na stejné úrovni aktivity dokončen. Ladicí program pak dělí na nadřazené aktuální aktivity. Když zanoříte z obslužnou rutinu kódu, ladicího programu dělí na aktivitu, ke kterému je přiřazeno obslužná rutina.

- **Krokovat s přeskočením**: Krok přes aktivitu stisknutím **F10**. Když krokování přes složených aktivit, ladicího programu dělí na prvním podřízeným objektem spustitelné složené aktivity. Když krokování přes jiný složené, například <xref:System.Activities.Statements.Assign> aktivity, ladicí program spustí aktivita a její přidružené obslužné rutiny a zalomení na další aktivitu. Pokud aktivita, která se spustí poslední podřízené aktivity ve složených aktivit, pak po spuštění, ladicího programu dělí na nadřazené aktivity.

## <a name="debug-with-f5"></a>Ladění pomocí F5

Pokud vytváříte konzolovou aplikaci pracovního postupu, jednoduše stiskněte **F5** zahájíte ladění do své aplikace a pracovní postup. Pokud vytváříte knihovna aktivit sama o sobě, musíte zadat aplikaci spustitelný soubor hostitele jako spouštěný projekt. Chcete-li nastavit spouštěný projekt **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu hostitele a vyberte **nastavit jako spouštěný projekt**.