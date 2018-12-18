---
title: 'Postupy: ladění rozhraní .NET Framework zdroje | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 234d9979ea1a16b917111e2a8937ad71dd55224f
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389277"
---
# <a name="how-to-debug-net-framework-source"></a>Postupy: ladění .NET Framework – zdroj

Ladění zdroje rozhraní .NET Framework, musíte mít:

- Povolte vstup do zdroje rozhraní.NET Framework.  
  
- Máte přístup k symbolům ladění pro kód. 
  
  Je možné stáhnout symboly ladění okamžitě, nebo nastavte možnosti pro pozdější stažení. Pokud nestáhnete symboly ihned, stáhnou se při příštím spuštění ladění vaší aplikace. Při ladění, můžete použít také **moduly** nebo **zásobník volání** windows ke stažení a načíst symboly.  
  
### <a name="to-enable-stepping-into-net-framework-source"></a>Povolit vstup do zdroje rozhraní.NET Framework 
  
1. V části **nástroje** (nebo **ladění**) > **možnosti** > **ladění** > **Obecné**vyberte **zdroje povolit rozhraní .NET Framework krokování**.  
   
   - Pokud jste měli povoleným kódem Just My, dialogové okno upozornění zjistíte, že funkce pouze můj kód je nyní zakázána. Vyberte **OK**.  
   
   - Pokud nemáte nastavení mezipaměti místního symbolu, dialogové okno upozornění zjistíte, že byla nastavena výchozí mezipaměti symbolů. Vyberte **OK**.  
   
1. Vyberte **OK** zavřete **možnosti** dialogového okna.
  
### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Nastavit nebo změnit zdroj umístění symbolu a chování načítání

1. Vyberte **symboly** kategorie v části **nástroje** (nebo **ladění**) > **možnosti** > **ladění**.  
  
1. Na **symboly** stránce v části **Symbol umístění souborů (.pdb)** vyberte **Microsoft Symbol Servers** symboly přístup z veřejné symbolové servery společnosti Microsoft. Vyberte tlačítko Přidat další umístění symbolů a změnit pořadí načítání. 
   
1. Chcete-li změnit váš místní symboly mezipaměti, upravit nebo můžete procházet do jiného umístění v rámci **mezipaměti symbolů v tomto adresáři**.  
   
1. Chcete-li stáhnout symboly hned, vyberte **načtení všech symbolů**. Toto tlačítko je k dispozici pouze při ladění.  
   
   Pokud není nyní nestahovat symboly, budete se stáhnou při příštím spuštění ladění.  
   
1. Vyberte **OK** zavřete **možnosti** dialogového okna.  
  
### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Načíst symboly z modulů nebo zásobník volání systému windows  
  
1. Během ladění, otevřete okno tak, že vyberete **ladění** > **Windows** > **moduly** nebo **zásobník volání** . 
   
1. Klikněte pravým tlačítkem na modul, pro který nejsou načteny symboly. V **moduly** , stav načítání symbolů je okno **symboly stavu** sloupce. V **zásobník volání** okna, stav je **stav rámce** sloupce a rámeček zobrazena šedě. 
   
   - Vyberte **načíst symboly** z nabídky pro vyhledání a načtení souborů ze složky na svém počítači. 
   
   - Vyberte **informace o načítání symbolů** zobrazíte umístění ladicí program hledá symboly.  
   
   - Vyberte **nastavení symbolu** otevřít **symboly** stránky. Na **symboly** stránce v části **Symbol umístění souborů (.pdb)** vyberte **Microsoft Symbol Servers** symboly přístup z veřejné symbolové servery společnosti Microsoft. Vyberte tlačítko Přidat další umístění symbolů a změnit pořadí načítání. Vyberte **OK** zavřete dialogové okno. 
  
### <a name="see-also"></a>Viz také:  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)