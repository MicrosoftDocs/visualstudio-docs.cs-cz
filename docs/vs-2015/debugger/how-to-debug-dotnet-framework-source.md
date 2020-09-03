---
title: 'Postupy: ladění zdroje .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205444"
---
# <a name="how-to-debug-net-framework-source"></a>Postupy: Ladění zdroje rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější verze nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje nové funkce pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ladění. Chcete-li ladit [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zdroj, je nutné mít přístup ke symbolům ladění kódu. Také je nutné povolit krokování do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zdroje.  
  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Krokování a stahování symbolů můžete povolit v dialogovém okně **Možnosti** . Pokud povolíte stahování symbolů, můžete si stáhnout symboly hned nebo povolit možnost pro pozdější stahování. Pokud symboly nestahujete okamžitě, budou se při příštím spuštění ladění aplikace stahovat symboly. Ruční stažení můžete provést také z okna **moduly** nebo z okna **zásobník volání** .  
  
### <a name="to-enable-net-framework-source-debugging"></a>Povolení ladění zdrojového kódu .NET Framework  
  
1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
2. V dialogovém okně **Možnosti** klikněte na kategorii **ladění** .  
  
3. V poli **Obecné** nastavte **možnost Povolit** krokování zdroje .NET Framework.  
  
    1. Pokud jste Pouze můj kód povolili, zobrazí se dialogové okno s upozorněním, že Pouze můj kód je teď zakázané. Klikněte na **OK**.  
  
    2. Pokud jste nenastavili umístění mezipaměti symbolů, další dialogové okno s upozorněním vás upozorní, že je teď nastavené výchozí umístění mezipaměti symbolů. Klikněte na **OK**.  
  
4. V kategorii **ladění** klikněte na **symboly**.  
  
5. Pokud chcete změnit umístění mezipaměti symbolů:  
  
    1. Otevřete uzel **ladění** v poli vlevo.  
  
    2. V uzlu **ladění** klikněte na **symboly**.  
  
    3. Upravte umístění v **symbolech mezipaměti ze serverů symbolů do tohoto adresáře** nebo klikněte na tlačítko **Procházet** a vyberte umístění.  
  
6. Pokud chcete symboly stáhnout hned, klikněte na **načíst symboly pomocí výše uvedených umístění**.  
  
     Toto tlačítko není k dispozici v režimu návrhu.  
  
     Pokud se nerozhodnete stahovat symboly nyní, symboly budou staženy automaticky při příštím spuštění ladění programu.  
  
7. Kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti** .  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Načtení symbolů rozhraní pomocí okna moduly  
  
1. V okně **moduly** klikněte pravým tlačítkem myši na modul, pro který nejsou načteny symboly. Můžete zjistit, jestli jsou symboly načtené, nebo ne, a to tak, že prohlížíte sloupec **stav symbolů** .  
  
2. Najeďte na **načíst symboly z** a kliknutím na **Microsoft symbol** Servers Stáhněte symboly ze serveru veřejných symbolů Microsoftu nebo **cesty k symbolům** pro načtení z adresáře, ve kterém jste předtím uložili symboly.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Načtení symbolů rozhraní pomocí okna zásobník volání  
  
1. V okně **zásobník volání** klikněte pravým tlačítkem myši na rámec, pro který nejsou načteny symboly. Rámec bude ztlumený.  
  
2. Přejděte na **načíst symboly z** a klikněte na **Microsoft Symbol Servers** nebo **cesta k symbolu**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
