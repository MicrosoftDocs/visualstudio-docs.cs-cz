---
title: Referenční informace o symbolech systému Windows | Microsoft Docs
description: Přečtěte si, jak aplikace Visual Studio Nástroje pro profilaci použít soubory symbolů (PDB) k překladu symbolických názvů, jako jsou názvy funkcí v binárních souborech programu.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: af194a324840bc3e8b8e67199c7e213d7dca96c9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720680"
---
# <a name="how-to-reference-windows-symbol-information"></a>Postupy: Odkazování na informace o symbolech Windows
Visual Studio Nástroje pro profilaci použít symbol (.*soubory PDB*) k překladu symbolických názvů, například názvů funkcí v binárních souborech programu. Pomocí těchto kroků můžete automaticky stáhnout a aktualizovat správné. soubory *PDB* pro verzi systému Windows v místním počítači.

> [!NOTE]
> Toto nastavení nemá vliv na existující sestavy. Informace o symbolu budou obsahovat pouze sestavy vytvořené po zadání serveru symbolů.

 Další informace najdete v tématu [určení symbolu (.*PDB*) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Používání serveru Microsoft symbol server

1. Vytvořte složku, která bude obsahovat informace o souboru symbolů, například C:\SymbolCache.

2. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

     Zobrazí se dialogové okno **Možnosti** .

3. Rozbalte strom **ladění** a potom klikněte na **symboly**.

4. V **umístění souborů symbolů (. pdb)** vyberte **Microsoft Symbol Servers** .

5. Do pole **symboly mezipaměti ze serveru symbolů do tohoto adresáře** zadejte cestu ke složce, která byla vytvořena v kroku 1, například:

     **C:\SymbolCache**

     Můžete také kliknout na tlačítko se třemi tečkami (**...**) a pak vybrat adresář v dialogovém okně **Vyhledat složku** .

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Postupy: serializace informací o symbolu](../profiling/how-to-serialize-symbol-information.md)
