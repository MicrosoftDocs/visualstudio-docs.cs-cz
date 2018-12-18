---
title: 'Postupy: referenční informace o symbolech Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ace6b0eaf71b4bfb992d0ff0ccdb09351eac2c19
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844167"
---
# <a name="how-to-reference-windows-symbol-information"></a>Postupy: odkaz na Windows symbolů informace
Visual Studio Tools profilace použít znak (. *pdb*) soubory přeložil symbolické názvy, jako funkce názvy v binárních souborů programu. Můžete provést tyto kroky automaticky stáhnout a aktualizovat správný. *pdb* soubory pro verzi systému Windows v místním počítači.  
  
> [!NOTE]
>  Toto nastavení nemá vliv na existující sestavy. Pouze sestavy vytvořené po zadání serveru symbol bude mít informací o symbolu.  
  
 Další informace najdete v tématu [zadání symbolu (. *pdb*) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Použití serveru Microsoft – symbol  
  
1.  Vytvořte složku tak, aby obsahovala symbol informací o souboru, jako je například C:\SymbolCache.  
  
2.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
     **Možnosti** zobrazí se dialogové okno.  
  
3.  Rozbalte **ladění** stromu a pak klikněte na **symboly**.  
  
4.  V **symbolů umístění souborů (.pdb)**, vyberte **servery Microsoft symbolů**  
  
5.  V **mezipaměti symboly ze serveru symbol do tohoto adresáře**, zadejte cestu ke složce, který byl vytvořen v kroku 1, například:  
  
     **C:\SymbolCache**  
  
     Můžete také kliknutím tlačítko se třemi tečkami (**...** ) a poté vyberte adresář z **vyhledat složku** dialogové okno.  
  
## <a name="see-also"></a>Viz také:  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Postupy: Serializace informací o symbolu](../profiling/how-to-serialize-symbol-information.md)