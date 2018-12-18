---
title: 'Postupy: ladění optimalizovaného kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6e212129c17ec7b4fe6cb9a6808c91cb302deb3
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52387859"
---
# <a name="how-to-debug-optimized-code"></a>Postupy: Ladění optimalizovaného kódu

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> [/Zo (vylepšit optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging)– možnost kompilátoru (představíme v sadě Visual Studio Update 3) generuje rozsáhlejší informace ladění pro optimalizovaný kód (projekty, které nejsou sestaveny s **/Od** – možnost kompilátoru. Zobrazit [/O možnosti (Optimalizace kódu)](/cpp/build/reference/o-options-optimize-code)). To zahrnuje Vylepšená podpora ladění lokálních proměnných a vložené funkce.
>
> [Upravit a pokračovat](../debugger/edit-and-continue-visual-csharp.md) vypnutá při **/Zo** ocompiler možnost se používá.

 Když kompilátor optimalizuje kód, přemístí a změní uspořádání pokyny. Výsledkem je účinnější zkompilovaný kód. Z důvodu této změny uspořádání ladicí program nemůže vždy identifikovat zdrojový kód, který odpovídá sadu pokynů.

 Může mít vliv na optimalizace:

- Lokální proměnné, které mohou být odebrána optimalizátorem nebo přesunout do umístění, které ladicí program nerozumí.

- Pozice uvnitř funkce, které se mění při Optimalizátor sloučí bloky kódu.

- Názvy funkcí pro rámce v zásobníku volání, které mohou být další potíže, pokud Optimalizátor Sloučí dvě funkce.

  Rámce, které se zobrazí v zásobníku volání jsou téměř vždy správná, ale za předpokladu, že máte symbolů pro všechny snímky. Pokud máte poškození zásobníku, pokud máte funkce v jazyce sestavení, nebo pokud jsou snímky operačního systému bez odpovídající symboly v zásobníku volání, bude nesprávný rámce v zásobníku volání.

  Globální a statické proměnné jsou vždy uvedeny správně. Proto je rozložení struktury. Pokud máte ukazatel na strukturu a hodnota ukazatele je správné, bude každé členské proměnné struktury zobrazení správné hodnoty.

  Kvůli těmto omezením by měl ladit, pokud možno používá neoptimalizované verzi programu. Ve výchozím nastavení optimalizace je vypnuta konfigurace ladění programu v jazyce Visual C++ a zapnuté v konfiguraci vydané verze.

  Chyba může být však zobrazí pouze v optimalizovanou verzi programu. V takovém případě musíte ladit optimalizovaný kód.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Chcete-li konfiguraci sestavení optimalizace ladění

1. Když vytvoříte nový projekt, vyberte `Win32 Debug` cíl. Použití `Win32``Debug` cílit, dokud se plně ladění programu a jste připraveni k sestavení `Win32 Release` cíl. Kompilátor neoptimalizuje `Win32 Debug` cíl.

2. Vyberte projekt v Průzkumníku řešení.

3. Na **zobrazení** nabídky, klikněte na tlačítko **stránky vlastností**.

4. V **stránky vlastností** dialogové okno pole, ujistěte se, že `Debug` výběru v **konfigurace** rozevíracího seznamu.

5. V zobrazení složky na levé straně vyberte **C/C++** složky.

6. V části **C++** složky, vyberte `Optimization`.

7. V seznamu vlastnosti na pravé straně najít `Optimization`. Nastavení vedle sebe pravděpodobně říká `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Vyberte jednu z dalších možností (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`, nebo `Custom`).

8. Pokud jste zvolili `Custom` možnost `Optimization`, teď můžete nastavit možnosti pro všechny ostatní vlastnosti zobrazené v seznamu vlastností.

9. Vyberte konfigurační vlastnosti, C/C++, uzel příkazového řádku na stránce Vlastnosti projektu a přidejte `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` k **další možnosti** textového pole.

    > [!WARNING]
    >  `/Zo` vyžaduje Visual Studio 2013 Update 3 nebo novější.
    >
    >  Přidání `/Zo` dojde k zakázání [upravit a pokračovat](../debugger/edit-and-continue-visual-csharp.md).

   Když ladíte optimalizovaný kód, použijte **zpětný překlad** okně zobrazíte pokyny, které jsou ve skutečnosti vytvářejí a. Při nastavení zarážek, je potřeba vědět, že zarážka může být přesunout společně s instrukce. Zvažte například následující kód:

```cpp
for (x=0; x<10; x++)
```

 Předpokládejme, že jste nastavili zarážku na tomto řádku. Očekáváte zarážce 10krát, ale pokud je optimalizovaný kód, zarážka se projeví pouze jednou. Důvodem je, že první instrukce nastaví hodnotu `x` na hodnotu 0. Kompilátor rozpozná, že to jenom je třeba provést jednou a přesouvá ji ze smyčky. Zarážka se přesune s ním. Pokyny, které porovnání a zvýší `x` zůstávají uvnitř smyčky. Při prohlížení **zpětný překlad** okně [jednotku kroku](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) se automaticky nastaví na instrukci pro větší kontrolu, což je užitečné, když krokovat optimalizovaný kód.

## <a name="see-also"></a>Viz také:

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)