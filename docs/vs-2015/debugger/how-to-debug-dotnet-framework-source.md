---
title: 'Postupy: ladění zdroje rozhraní .NET Framework | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce5e20524040d131a655da1567606ffbb0934a80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725424"
---
# <a name="how-to-debug-net-framework-source"></a>Postupy: Ladění zdroje rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Překopírujte nejnovější verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsahuje nové funkce pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ladění. Chcete-li ladit [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zdroje, musíte mít přístup k symbolům ladění pro kód. Je také potřeba povolit krokování s vnořením do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zdroje.  
  
 Můžete povolit [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] kroky a stahování v symbolu **možnosti** dialogové okno. Když povolíte stahování symbolů, můžete stáhnout symboly hned nebo Povolit jenom možnost pro pozdější stažení. Pokud okamžitě nestáhnete symboly, symboly budou staženy při příštím spuštění ladění vaší aplikace. Můžete také provést ruční stažení z **moduly** okno nebo **zásobník volání** okna.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Chcete-li povolit ladění zdrojového kód rozhraní .NET Framework  
  
1.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
2.  V **možnosti** dialogové okno, klikněte na tlačítko **ladění** kategorie.  
  
3.  V **Obecné** pole, nastavte **povolit rozhraní .NET Framework** krokování zdrojových kódů.  
  
    1.  Pokud jste měli povoleným kódem Just My, dialogové okno upozornění zjistíte, že funkce pouze můj kód je nyní zakázána. Klikněte na tlačítko **OK**.  
  
    2.  Pokud nastaveno umístění mezipaměti symbolů, jiné dialogové okno upozornění informuje, že výchozí umístění mezipaměti symbolů je nyní nastaveno. Klikněte na tlačítko **OK**.  
  
4.  V části **ladění** kategorii, klikněte na tlačítko **symboly**.  
  
5.  Pokud chcete změnit umístění mezipaměti symbolů:  
  
    1.  Otevřít **ladění** uzlu v poli na levé straně.  
  
    2.  V části **ladění** uzel, klikněte na tlačítko **symboly**.  
  
    3.  Upravit umístění v **mezipaměti symbolů ze serverů symbolů do tohoto adresáře** nebo klikněte na tlačítko **Procházet** k výběru umístění.  
  
6.  Pokud chcete stáhnout symboly hned, klikněte na tlačítko **načíst symboly pomocí výše uvedených umístění**.  
  
     Toto tlačítko není k dispozici v režimu návrhu.  
  
     Pokud nevyberete nyní nestahovat symboly, symboly budou staženy automaticky při příštím spuštění ladění programu.  
  
7.  Klikněte na tlačítko **OK** zavřete **možnosti** dialogové okno.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Načtení symbolů rozhraní pomocí okna modulů  
  
1.  V **moduly** okna, klikněte pravým tlačítkem na modul, pro který nejsou načteny symboly. Poznáte, zda jsou načteny symboly nebo není zobrazením **symboly stavu** sloupce.  
  
2.  Přejděte na **načíst symboly z** a klikněte na tlačítko **Microsoft Symbol Servers** ke stažení symbolů ze serveru veřejných symbolů Microsoft nebo **cesty k symbolu** načtení z adresáře Pokud jste dříve uložili symboly.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Načtení symbolů rozhraní pomocí okna zásobník volání  
  
1.  V **zásobník volání** okna, klikněte pravým tlačítkem na rámec, pro který nejsou načteny symboly. Snímek bude znepřístupněn.  
  
2.  Přejděte na **načíst symboly z** a klikněte na tlačítko **Microsoft Symbol Servers** nebo **cesty k symbolu**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



