---
title: Vytvoření Mini výpisy se všemi zásobníky volání
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271183"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Vytvoření Mini výpisy pro proces sady Visual Studio se všemi zásobníky volání

V některých případech může společnost Microsoft požádat o s minimálním výpisem spuštěného procesu sady Visual Studio s informacemi pro všechny zásobníky volání. Chcete-li shromáždit tyto informace, proveďte tyto kroky:

## <a name="create-the-minidump-file"></a>Vytvoření souboru s minimálním výpisem

1. Spusťte novou instanci sady Visual Studio.
1. V hlavní nabídce vyberte možnost **ladění** > **připojit k procesu**.
1. Zaškrtněte příslušná **spravovaná** a **nativní** zaškrtávací políčka a stiskněte **připojit**.

   ![Připojení k procesu](../ide/media/attach-to-process.png)

1. Vyberte jinou instanci sady Visual Studio, kterou chcete připojit, ze seznamu spuštěných procesů.
1. V hlavní nabídce vyberte možnost **ladit** > **přerušit vše**.
1. V hlavní nabídce vyberte položku **ladění** > **Uložit výpis paměti jako**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Získat zásobníky volání z s minimálním výpisem

1. Otevřete soubor s výpisem paměti v aplikaci Visual Studio.
1. V části **nástroje** > **možnosti** > **ladění** > **symboly** a ujistěte se, že jsou v **umístění souborů symbolů (. pdb)** zaškrtnuté políčko **Microsoft symbol server** .
1. Otevřete okno **příkazového** řádku (**Zobrazit** > jiné **okno příkazového** > **systému Windows** ).
1. Typ ~ * k. V okně se zobrazí všechny zásobníky volání vláken.
1. Zkopírujte veškerý text z příkazového okna a uložte ho do textového souboru.
1. Připojte soubor txt k chybě.
