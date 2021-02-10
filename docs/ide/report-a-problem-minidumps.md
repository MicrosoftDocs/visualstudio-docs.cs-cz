---
title: Vytvoření Mini výpisy se všemi zásobníky volání
description: Naučte se, jak vytvořit Mini výpisy pro proces sady Visual Studio, který obsahuje informace pro všechny zásobníky volání.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 44ab0873580c7c541fc5e7fdde56cc1780929b75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970774"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Vytvoření Mini výpisy pro proces sady Visual Studio se všemi zásobníky volání

V některých případech může společnost Microsoft požádat o s minimálním výpisem spuštěného procesu sady Visual Studio s informacemi pro všechny zásobníky volání. Chcete-li shromáždit tyto informace, proveďte tyto kroky:

## <a name="create-the-minidump-file"></a>Vytvoření souboru s minimálním výpisem

1. Spusťte novou instanci sady Visual Studio.
1. V hlavní nabídce vyberte možnost **ladit**  >  **připojit k procesu**.
1. Zaškrtněte příslušná **spravovaná** a **nativní** zaškrtávací políčka a stiskněte **připojit**.

   ![Připojení k procesu](../ide/media/attach-to-process.png)

1. Vyberte jinou instanci sady Visual Studio, kterou chcete připojit, ze seznamu spuštěných procesů.
1. V hlavní nabídce vyberte možnost **ladit**  >  **přerušit vše**.
1. V hlavní nabídce klikněte na položku **ladit**  >  **Uložit výpis paměti jako**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Získat zásobníky volání z s minimálním výpisem

1. Otevřete soubor s výpisem paměti v aplikaci Visual Studio.
1. Přejdete na **nástroje**  >  **Možnosti**  >  **ladění**  >  **symboly** a ujistěte se, že jsou v **umístění souborů symbolů (. pdb)** zaškrtnuté políčko **servery symbolů společnosti Microsoft** .
1. Otevřete okno **příkazového** řádku (**Zobrazit**  >  **jiné**  >  **příkazové okno** systému Windows).
1. Typ ~ * k. V okně se zobrazí všechny zásobníky volání vláken.
1. Zkopírujte veškerý text z příkazového okna a uložte ho do textového souboru.
1. Připojte soubor txt k chybě.
