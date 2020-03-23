---
title: 'Postup: Odkaz na informace o symbolu systému Windows | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 28bbd4b584d679c03c58ba8532ced3f28f16d6aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774910"
---
# <a name="how-to-reference-windows-symbol-information"></a>Postupy: Odkazování na informace o symbolech Windows
Nástroje profilování visual studia používají symbol (.* pdb*) k překladu symbolických názvů, jako jsou názvy funkcí v binárních souborech programů. Pomocí těchto kroků můžete automaticky stáhnout a aktualizovat správné . *pdb* pro verzi systému Windows v místním počítači.

> [!NOTE]
> Toto nastavení nemá vliv na existující sestavy. Pouze sestavy vytvořené po zadání serveru symbolů budou mít informace o symbolech.

 Další informace naleznete [v tématu Specify symbol (.* pdb*) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Použití symbolového serveru společnosti Microsoft

1. Vytvořte složku, která bude obsahovat informace o souboru symbolu, například C:\SymbolCache.

2. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

     Zobrazí se dialogové okno **Možnosti.**

3. Rozbalte strom **ladění** a klepněte na **symboly**.

4. V **umístění souboru Symbol (.pdb)** vyberte **položku Microsoft Symbol Servers**

5. Do **symbolů mezipaměti ze serveru symbolů do tohoto adresáře**zadejte cestu ke složce, která byla vytvořena v kroku 1, například:

     **C:\SymbolCache**

     Můžete také klepnout na tlačítko se třemi tečkami (**...**) a pak vybrat adresář z dialogového okna **Vyhledat složku.**

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Postup: Serializace informací o symbolech](../profiling/how-to-serialize-symbol-information.md)
