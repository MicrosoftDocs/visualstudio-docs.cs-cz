---
title: Vytvoření minidumpů se všemi zásobníky volání
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271183"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Vytvoření minidumpů pro proces sady Visual Studio se všemi zásobníky volání

V některých případech může společnost Microsoft požádat o minidump spuštěného procesu sady Visual Studio s informacemi pro všechny zásobníky volání. Chcete-li tyto informace shromáždit, proveďte následující kroky:

## <a name="create-the-minidump-file"></a>Vytvoření souboru minidump

1. Spusťte novou instanci sady Visual Studio.
1. V hlavní nabídce zvolte **Ladit** > **připojit ke zpracování**.
1. Zaškrtněte **příslušná spravovaná** a **nativní** políčka a stiskněte **tlačítko Připojit**.

   ![Připojení k procesu](../ide/media/attach-to-process.png)

1. Vyberte jinou instanci sady Visual Studio, ke které chcete připojit ze seznamu spuštěných procesů.
1. V hlavní nabídce zvolte **Ladění** > **zalomení všech**.
1. V hlavní nabídce zvolte **Debug** > **Save Dump As**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Získejte zásobníky volání z minidumpu

1. Otevřete soubor výpisu v sadě Visual Studio.
1. Přejděte na**možnosti** >  **nástrojů** > **Ladění** > **symbolů** a ujistěte se, že **servery Symbol společnosti Microsoft** jsou kontrolovány v umístění **souboru symbolů (.pdb).**
1. Otevření **okna Příkaz** **(Zobrazit** > další**okno s příkazy systému****Windows** > )
1. Zadejte '~*k'. V okně se zobrazí všechny zásobníky volání všech vláken.
1. Zkopírujte veškerý text z příkazového okna a uložte jej do textového souboru.
1. Připojte soubor txt k chybě.
