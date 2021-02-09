---
title: Ladění optimalizovaného kódu | Microsoft Docs
description: Pokud je to možné, nevytvářejte cíl verze Win32, dokud nebude program laděn, protože optimalizace může zkomplikovat ladění. Přečtěte si podrobnosti v tomto článku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19b09831aea0f7e38c7d095c1e549496569405c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899305"
---
# <a name="how-to-debug-optimized-code"></a>Postupy: Ladění optimalizovaného kódu

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> Možnost kompilátoru [/Zo (vylepšit optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging)(představená v aktualizaci Visual Studio Update 3) generuje bohatší informace ladění pro optimalizovaný kód (projekty, které nejsou sestavené pomocí možnosti kompilátoru **/od** . Viz [Možnosti/o (optimalizace kódu)](/cpp/build/reference/o-options-optimize-code)). To zahrnuje vylepšenou podporu pro ladění místních proměnných a vložené funkce.
>
> Možnost [Upravit a pokračovat](../debugger/edit-and-continue-visual-csharp.md) je zakázána při použití možnosti **/Zo** ocompiler.

 Když kompilátor optimalizuje kód, přemístí a reorganizuje pokyny. Výsledkem je efektivnější zkompilovaný kód. Kvůli této změně uspořádání nemůže ladicí program vždy identifikovat zdrojový kód, který odpovídá sadě instrukcí.

 Optimalizace může ovlivnit:

- Místní proměnné, které lze odebrat optimalizátorem nebo přesunout do umístění, které ladicí program nerozumí.

- Pozice uvnitř funkce, které se změní, když Optimalizátor slučuje bloky kódu.

- Názvy funkcí pro rámce v zásobníku volání, které mohou být nesprávné, pokud Optimalizátor sloučí dvě funkce.

  Rámce, které vidíte v zásobníku volání, jsou téměř vždy správné, ale za předpokladu, že máte symboly pro všechny snímky. Snímky v zásobníku volání budou nesprávné, pokud máte poškozený zásobník, pokud máte funkce napsané v jazyce sestavení nebo pokud existují snímky operačního systému bez odpovídajícího symbolu v zásobníku volání.

  Globální a statické proměnné jsou vždy zobrazeny správně. Takže je rozložení struktury. Pokud máte ukazatel na strukturu a hodnota ukazatele je správná, zobrazí se v každé členské proměnné struktury správná hodnota.

  Z důvodu těchto omezení byste měli ladit pomocí neoptimalizované verze programu, pokud je to možné. Ve výchozím nastavení je optimalizace vypnuta v konfiguraci ladění programu v jazyce C++ a je zapnutá v konfiguraci vydané verze.

  Chyba se však může zobrazit pouze v optimalizované verzi programu. V takovém případě je nutné ladit optimalizovaný kód.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Zapnutí optimalizace v konfiguraci sestavení ladění

1. Když vytvoříte nový projekt, vyberte `Win32 Debug` cíl. Použijte `Win32 Debug` cíl, dokud nebude program plně laděn a jste připraveni vytvořit `Win32 Release` cíl. Kompilátor neoptimalizuje `Win32 Debug` cíl.

2. Vyberte projekt v Průzkumník řešení.

3. V nabídce **zobrazení** klikněte na položku **stránky vlastností**.

4. V dialogovém okně **stránky vlastností** se ujistěte, že `Debug` je vybrána možnost v rozevíracím seznamu **Konfigurace** .

5. V zobrazení složky na levé straně vyberte složku **C/C++** .

6. Ve složce **C++** vyberte `Optimization` .

7. V seznamu vlastností vpravo Najděte `Optimization` . Nastavení vedle něj pravděpodobně říká `Disabled (` [/od](/cpp/build/reference/od-disable-debug) `)` . Vyberte jednu z dalších možností ( `Minimum Size``(` [/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)` nebo `Custom` ).

8. Pokud jste zvolili `Custom` možnost pro `Optimization` , můžete nyní nastavit možnosti pro kteroukoli z dalších vlastností, které jsou uvedeny v seznamu vlastností.

9. Vyberte uzel vlastnosti konfigurace, C/C++, příkazový řádek stránky vlastností projektu a přidejte `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` do textového pole **Další možnosti** .

    > [!WARNING]
    > `/Zo` vyžaduje Visual Studio 2013 Update 3 nebo novější verzi.
    >
    >  Při přidání `/Zo` se zakáže [Úpravy a pokračování](../debugger/edit-and-continue-visual-csharp.md).

   Při ladění optimalizovaného kódu použijte okno **zpětný překlad** k zobrazení pokynů, které jsou skutečně vytvořeny a provedeny. Při nastavování zarážek je nutné znát, zda se zarážka může pohybovat spolu s instrukcí. Zvažte například následující kód:

```cpp
for (x=0; x<10; x++)
```

 Předpokládejme, že jste na tomto řádku nastavili zarážku. Můžete očekávat, že zarážka bude dosaženo 10 krát, ale pokud je kód optimalizován, zarážka se narazí pouze jednou. Důvodem je, že první instrukce nastaví hodnotu `x` na 0. Kompilátor rozpozná, že je nutné provést pouze jednou a přesune ho mimo smyčku. Zarážka se přesune s ním. Pokyny, které porovnávají a zvyšovat, `x` zůstávají uvnitř smyčky. Když zobrazíte okno **zpětný překlad** , [jednotka kroku](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) je automaticky nastavena na instrukci pro větší kontrolu, což je užitečné při Krokovat s použitím optimalizovaného kódu.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)