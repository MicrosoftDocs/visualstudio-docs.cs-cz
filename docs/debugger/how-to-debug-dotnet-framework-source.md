---
title: .NET Framework zdroj ladění | Microsoft Docs
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f054564ff36c538b18525ec9d8adf9b6f3d060b9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852123"
---
# <a name="how-to-debug-net-framework-source"></a>Postupy: ladění zdroje .NET Framework

Chcete-li ladit zdroj .NET Framework, musíte:

- Umožňuje zapnout krokování do zdroje .NET Framework.

- Mít přístup ke symbolům ladění pro kód.

  Můžete si zvolit, že se symboly ladění mají hned stáhnout, nebo nastavit možnosti pro pozdější stažení. Pokud symboly nestahujete hned, stáhne se při příštím spuštění ladění aplikace. Při ladění můžete také použít **moduly** nebo okna **zásobníku volání** ke stažení a načtení symbolů.

### <a name="to-enable-stepping-into-net-framework-source"></a>Postup povolení krokování do zdroje .NET Framework

1. V části **nástroje** (nebo **ladění**) > **Možnosti**  >  **ladění**  >  **obecně**vyberte **Povolit .NET Framework krokování zdroje**.

   - Pokud jste Pouze můj kód povolili, zobrazí se dialogové okno s upozorněním, že Pouze můj kód je teď zakázané. Vyberte **OK**.

   - Pokud jste nenastavili místní mezipaměť symbolů, zobrazí se dialogové okno s upozorněním, že byla nastavena výchozí mezipaměť symbolů. Vyberte **OK**.

1. Kliknutím na **tlačítko OK** zavřete dialogové okno **Možnosti** .

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Nastavení nebo změna umístění zdroje symbolu a chování načítání

1. Vyberte kategorii **symboly** v nabídce **nástroje** (nebo **ladění**) > **Options**  >  **ladění**možností.

1. Na stránce **symboly** v části **umístění souborů symbolů (. pdb)** vyberte **Microsoft Symbol Servers** , abyste měli přístup k symbolům z veřejných serverů Microsoft symbol. Vyberte tlačítka panelu nástrojů pro přidání dalších umístění symbolů a změňte pořadí načítání.

1. Chcete-li změnit místní mezipaměť symbolů, upravte nebo vyhledejte jiné umístění v části **symboly mezipaměti v tomto adresáři**.

1. Chcete-li stáhnout symboly hned, vyberte **načíst všechny symboly**. Toto tlačítko je k dispozici pouze při ladění.

   Pokud symboly nestahujete nyní, budou staženy při příštím spuštění ladění.

1. Kliknutím na **tlačítko OK** zavřete dialogové okno **Možnosti** .

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Načtení symbolů z modulů nebo oken zásobníku volání

1. Během ladění otevřete okno výběrem možnosti **ladit**  >  moduly**systému Windows**  >  **Modules** (nebo stiskněte klávesy **CTRL + ALT + U**) nebo **laděním**  >  **Windows**  >  **zásobníku volání** systému Windows (**CTRL + ALT + C**).

1. Klikněte pravým tlačítkem na modul, pro který nejsou načtené symboly. V okně **moduly** je stav načítání symbolů ve sloupci **stav symbolů** . V okně **zásobník volání** je stav ve sloupci **stav rámce** a rámeček je šedý.

   - V nabídce vyberte **načíst symboly** , abyste našli a načetli soubory symbolů ze složky na vašem počítači.

   - Vyberte **informace o načtení symbolů** pro zobrazení umístění, ve kterém ladicí program hledal symboly.

   - Vyberte **Nastavení symbolu** a otevřete stránku **symboly** . Na stránce **symboly** v části **umístění souborů symbolů (. pdb)** vyberte **Microsoft Symbol Servers** , abyste měli přístup k symbolům z veřejných serverů Microsoft symbol. Vyberte tlačítka panelu nástrojů pro přidání dalších umístění symbolů a změňte pořadí načítání. Kliknutím na **tlačítko OK** zavřete dialogové okno.

### <a name="see-also"></a>Viz také
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)