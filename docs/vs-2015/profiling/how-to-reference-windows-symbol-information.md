---
title: 'Postupy: odkazování na informace o symbolech Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7a123a42c1a46faf67fb5b63b1ab4ef300735f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822704"
---
# <a name="how-to-reference-windows-symbol-information"></a>Postupy: Referenční informace o symbolech Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace Visual Studio Nástroje pro profilaci použít soubory symbolů (PDB) k překladu symbolických názvů, například názvů funkcí v binárních souborech programu. Pomocí těchto kroků můžete automaticky stáhnout a aktualizovat správné soubory. PDB pro verzi systému Windows v místním počítači.  
  
> [!NOTE]
> Toto nastavení nemá vliv na existující sestavy. Informace o symbolu budou obsahovat pouze sestavy vytvořené po zadání serveru symbolů.  
  
 Další informace naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Používání serveru Microsoft symbol server  
  
1. Vytvořte složku, která bude obsahovat informace o souboru symbolů, například C:\SymbolCache.  
  
2. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
     Zobrazí se dialogové okno **Možnosti** .  
  
3. Rozbalte strom **ladění** a potom klikněte na **symboly**.  
  
4. V **umístění souborů symbolů (. pdb)** vyberte **Microsoft Symbol Servers** .  
  
5. Do pole **symboly mezipaměti ze serveru symbolů do tohoto adresáře**zadejte cestu ke složce, která byla vytvořena v kroku 1, například:  
  
     **C:\SymbolCache**  
  
     Můžete také kliknout na tlačítko se třemi tečkami (**...**) a pak vybrat adresář v dialogovém okně **Vyhledat složku** .  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Postupy: Serializace informací o symbolu](../profiling/how-to-serialize-symbol-information.md)
