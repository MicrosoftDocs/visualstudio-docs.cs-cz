---
title: Upravit a pokračovat (C++) | Microsoft Docs
ms.date: 05/31/2018
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9c32c161d1df70fc81eee4186aa9d1ac102afa69
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599650"
---
# <a name="edit-and-continue-c"></a>Upravit a pokračovat (C++)
V projektech v jazyce C++ můžete použít možnost upravit a pokračovat. Informace o omezeních pro úpravu a pokračování naleznete v tématu [podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md) .

Další informace o vylepšeních sady Visual Studio 2015 Update 3 najdete [v tématu Úprava a pokračování C++ v aplikaci Visual studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 Možnost kompilátoru [/Zo (rozšířené optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging) , která byla představena ve službě Visual Studio 2013 Update 3, přidává další informace do souborů. pdb (symbol) pro binární soubory kompilované bez možnosti [/od (Disable (Ladit))](/cpp/build/reference/od-disable-debug) .

 **/Zo** zakáže funkci upravit a pokračovat. Viz [How to: Debug optimalizovaného kódu](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Povolit nebo zakázat úpravy a pokračovat
 Pokud upravujete kód, který nechcete použít během aktuální relace ladění, je vhodné zakázat automatické vyvolání funkce upravit a pokračovat. Můžete také znovu povolit automatické úpravy a pokračovat.

> [!IMPORTANT]
> Pro požadovaná nastavení sestavení a další informace o kompatibilitě funkcí naleznete [v tématu úpravy a pokračování C++ v aplikaci Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Pokud jste v relaci ladění, zastavte ladění (**SHIFT + F5**).

2. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

3. V dialogovém okně **Možnosti** vyberte možnost **ladění > obecné**.

4. Pokud ho chcete povolit, vyberte **Povolit upravit a pokračovat**. Pokud ho chcete zakázat, zaškrtnutí políčka zrušte.

5. Ve skupině **Upravit a pokračovat** zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit nativní úpravu a pokračování** .

   Změna tohoto nastavení ovlivní všechny projekty, na kterých pracujete. Po změně tohoto nastavení nemusíte aplikaci znovu sestavovat. Při sestavování aplikace z příkazového řádku nebo ze souboru pravidel, ale ladění v prostředí Visual Studio, můžete i nadále používat možnost upravit a pokračovat, pokud nastavíte možnost **/Zi** .

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Explicitní použití změn kódu
 Příkaz Upravit a pokračovat může v jazyce C++ použít změny kódu dvěma způsoby. Změny kódu lze použít implicitně, pokud vyberete příkaz pro spuštění nebo explicitně pomocí příkazu **použít změny kódu** .

 Pokud použijete změny kódu explicitně, zůstane program v režimu pozastavení – nedojde k žádnému spuštění.

- Chcete-li použít změny kódu explicitně, v nabídce **ladění** vyberte možnost **použít změny kódu**.

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Zastavení změn kódu
 I když je proces úpravy a pokračování v procesu aplikování změn kódu, můžete operaci zastavit.

 Zastavení použití změn kódu:

- V nabídce **ladění** vyberte možnost **zastavit aplikování změn kódu**.

  Tato položka nabídky je viditelná pouze v případě, že jsou aplikovány změny kódu.

  Pokud zvolíte tuto možnost, není potvrzena žádná změna kódu.

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Postup obnovení bodu provádění
 Některé změny kódu můžou způsobit, že se bod spuštění přesune do nového umístění, když se změny upraví a pokračuje. Možnost upravit a pokračovat umístí místo spuštění co nejpřesněji, ale výsledky nemusí být ve všech případech správné.

 V jazyce C++ se zobrazí dialogové okno, když se změní bod provádění. Před pokračováním v ladění je vhodné ověřit, zda je umístění správné. Pokud není správný, použijte příkaz **nastavit další příkaz** . Další informace najdete v tématu [nastavení dalšího příkazu ke spuštění](./navigating-through-code-with-the-debugger.md#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Jak pracovat se zastaralým kódem
 V některých případech nemůže příkaz Upravit a pokračovat ve spustitelném souboru okamžitě použít změny kódu, ale po pokračování v ladění může být možné použít změny kódu později. K tomu dojde, pokud upravíte funkci, která volá aktuální funkci, nebo pokud do funkce v zásobníku volání přidáte více než 64 bajtů nových proměnných.

 V takových případech ladicí program pokračuje ve spouštění původního kódu, dokud se změny nedají použít. Zastaralý kód se zobrazí jako dočasné okno zdrojového souboru v samostatném zdrojovém okně s názvem, jako je například `enc25.tmp` . Upravovaný zdroj se nadále zobrazuje v původním okně zdrojového kódu. Pokud se pokusíte upravit zastaralý kód, zobrazí se varovná zpráva.

## <a name="see-also"></a>Viz také
- [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)