---
title: Upravit a pokračovat (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/31/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 7e468f75abbadbe46ea973a5c04d2e286fcfaca5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867699"
---
# <a name="edit-and-continue-visual-c"></a>Upravit a pokračovat (Visual C++)
Můžete upravit a pokračovat v projektech Visual C++. Zobrazit [podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md) informace o omezení operace upravit a pokračovat.
  
Další informace o vylepšení Visual Studio 2015 Update 3 najdete v tématu [C++ upravit a pokračovat v sadě Visual Studio 2015 Update 3](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/).  
  
 [/Zo (vylepšit optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging) – možnost kompilátoru, která byla zavedena v sadě Visual Studio 2013 Update 3 přidá do souborů s příponou .pdb (symbol) Další informace pro binární soubory zkompilovány bez volby [/Od (zakázat (ladění)) ](https://msdn.microsoft.com/library/aafb762y.aspx) možnost.  
  
 **/Zo** zakáže operace upravit a pokračovat. Zobrazit [postupy: ladění optimalizovaného kódu](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Povolení nebo zakázání funkce upravit a pokračovat  
 Můžete chtít zakázat automatického volání operace upravit a pokračovat, pokud provádíte úpravy kódu, který nechcete, aby platily aktuální relace ladění. Můžete také znovu povolit automatické funkce upravit a pokračovat.

> [!IMPORTANT]
> Nastavení požadovaná sestavení a další informace o kompatibilitě funkce najdete v tématu [C++ upravit a pokračovat v sadě Visual Studio 2015 Update 3] (https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/.
  
1. Pokud jste v relaci ladění, zastavte ladění (**Shift + F5**).

2. Na **nástroje** nabídce zvolte **možnosti**.
  
3. V **možnosti** dialogu **ladění > Obecné**.

4. Pokud chcete povolit, vyberte **Povolit Editovat a pokračovat**. Pokud chcete zakázat, zrušte zaškrtnutí políčka.
  
5. V **upravit a pokračovat** skupině, zaškrtněte nebo zrušte zaškrtnutí **Povolit nativní editovat a pokračovat** zaškrtávací políčko.  
  
   Změna tohoto nastavení má vliv na všechny projekty, které pracujete. Není nutné znovu sestavit aplikaci po změně tohoto nastavení. Pokud vytváříte aplikaci z příkazového řádku nebo ze souboru pravidel, ale ladit v prostředí sady Visual Studio, stále můžete upravit a pokračovat Pokud nastavíte **/zi** možnost.  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Jak explicitní použití změn kódu  
 V jazyce Visual C++ můžete použít kód změny v dva způsoby, jak upravit a pokračovat. Změny kódu lze použít implicitně, když zvolíte příkazu ke spuštění, nebo explicitně, pomocí **použít změny kódu** příkazu.  
  
 Při explicitní použití změn kódu aplikace zůstávají v režimu pozastavení – žádná spuštění.  
  
-   Na explicitní, použití změn kódu na **ladění** nabídce zvolte **použít změny kódu**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> Postup zastavení změn kódu  
 Upravit a pokračovat je právě aplikování změn kódu, můžete zastavit operaci.  
  
 Zastavit provádění změn kódu:  
  
- Na **ladění** nabídce zvolte **zastavit provádění změn kódu**.  
  
  Tato položka nabídky je viditelná pouze v případě, že se aplikují změny kódu.  
  
  Pokud zvolíte tuto možnost, žádná ze změn kódu není potvrzena.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Obnovení bodu provádění  
 Některé změny kódu může způsobit bod provádění přesunout do nového umístění, pokud funkce upravit a pokračovat se vztahuje změny. Upravit a pokračovat umístí bod provádění co nejpřesněji, ale výsledky nemusí být správný ve všech případech.  
  
 V jazyce Visual C++ dialogové okno vás informuje změny bodu provádění. Ověřte, že je umístění správné předtím, než budete pokračovat v ladění. Pokud není správná, použijte **nastavit další příkaz** příkazu. Další informace najdete v tématu [nastavení dalšího příkazu ke spuštění](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> Práce se starým kódem  
 V některých případech funkce upravit a pokračovat nemůže použití změn kódu spustitelný soubor, ale možná půjde použít změny kódu později, pokud budete pokračovat, ladění. K tomu dochází při úpravě funkce, která volá aktuální funkci nebo pokud chcete přidat více než 64 bajtů nové proměnné na funkci v zásobníku volání  
  
 V takových případech ladicí program pokračuje v provádění původní kód, dokud změny mohou být použity. Zastaralý kód se zobrazí jako dočasné zdrojové okno souborů v okně samostatného zdroje s názvem, jako `enc25.tmp`. Upravené zdroje i nadále zobrazovat v okně původního zdroje. Pokud se pokusíte úprava starý kód, zobrazí se zpráva s upozorněním.  
  
## <a name="see-also"></a>Viz také  
 [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)