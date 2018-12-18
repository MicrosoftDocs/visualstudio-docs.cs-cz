---
title: 'Postupy: ladění optimalizovaného kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3d0e6c86c800e2ba35fdac78d6659fa2ecd7e94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734055"
---
# <a name="how-to-debug-optimized-code"></a>Postupy: Ladění optimalizovaného kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

POZNÁMKA:]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  [/Zo (vylepšit optimalizované ladění)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)– možnost kompilátoru (představíme v sadě Visual Studio Update 3) generuje rozsáhlejší informace ladění pro optimalizovaný kód (projekty, které nejsou sestaveny s **/Od** – možnost kompilátoru. Zobrazit [/O možnosti (Optimalizace kódu)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)). To zahrnuje Vylepšená podpora ladění lokálních proměnných a vložené funkce.  
>   
>  [Upravit a pokračovat](../debugger/edit-and-continue-visual-csharp.md) vypnutá při **/Zo** ocompiler možnost se používá.  
  
 Když kompilátor optimalizuje kód, přemístí a změní uspořádání pokyny. Výsledkem je účinnější zkompilovaný kód. Z důvodu této změny uspořádání ladicí program nemůže vždy identifikovat zdrojový kód, který odpovídá sadu pokynů.  
  
 Může mít vliv na optimalizace:  
  
- Lokální proměnné, které mohou být odebrána optimalizátorem nebo přesunout do umístění, které ladicí program nerozumí.  
  
- Pozice uvnitř funkce, které se mění při Optimalizátor sloučí bloky kódu.  
  
- Názvy funkcí pro rámce v zásobníku volání, které mohou být další potíže, pokud Optimalizátor Sloučí dvě funkce.  
  
  Rámce, které se zobrazí v zásobníku volání jsou téměř vždy správná, ale za předpokladu, že máte symbolů pro všechny snímky. Pokud máte poškození zásobníku, pokud máte funkce v jazyce sestavení, nebo pokud jsou snímky operačního systému bez odpovídající symboly v zásobníku volání, bude nesprávný rámce v zásobníku volání.  
  
  Globální a statické proměnné jsou vždy uvedeny správně. Proto je rozložení struktury. Pokud máte ukazatel na strukturu a hodnota ukazatele je správné, bude každé členské proměnné struktury zobrazení správné hodnoty.  
  
  Kvůli těmto omezením by měl ladit, pokud možno používá neoptimalizované verzi programu. Ve výchozím nastavení optimalizace je vypnuta konfigurace ladění programu v jazyce Visual C++ a zapnuté v konfiguraci vydané verze.  
  
  Chyba může být však zobrazí pouze v optimalizovanou verzi programu. V takovém případě musíte ladit optimalizovaný kód.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Chcete-li konfiguraci sestavení optimalizace ladění  
  
1. Když vytvoříte nový projekt, vyberte `Win32 Debug` cíl. Použití `Win32``Debug` cílit, dokud se plně ladění programu a jste připraveni k sestavení `Win32 Release` cíl. Kompilátor neoptimalizuje `Win32 Debug` cíl.  
  
2. Vyberte projekt v Průzkumníku řešení.  
  
3. Na **zobrazení** nabídky, klikněte na tlačítko **stránky vlastností**.  
  
4. V **stránky vlastností** dialogové okno pole, ujistěte se, že `Debug` výběru v **konfigurace** rozevíracího seznamu.  
  
5. V zobrazení složky na levé straně vyberte **C/C++** složky.  
  
6. V části **C++** složky, vyberte `Optimization`.  
  
7. V seznamu vlastnosti na pravé straně najít `Optimization`. Nastavení vedle sebe pravděpodobně říká `Disabled (` [/Od](http://msdn.microsoft.com/library/b1ac31b7-e086-4eeb-be5e-488f7513f5f5)`)`. Vyberte jednu z dalších možností (`Minimum Size``(`[/O1](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Maximum Speed``(` [/O2](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Full Optimization``(` [/Ox](http://msdn.microsoft.com/library/3ad7c30b-c615-428c-b1d0-2e024f81c760) `)`, nebo `Custom`).  
  
8. Pokud jste zvolili `Custom` možnost `Optimization`, teď můžete nastavit možnosti pro všechny ostatní vlastnosti zobrazené v seznamu vlastností.  
  
9. Vyberte konfigurační vlastnosti, C/C++, uzel příkazového řádku na stránce Vlastnosti projektu a přidejte `(` [/Zo](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) `)` k **další možnosti** textového pole.  
  
    > [!WARNING]
    >  `/Zo` vyžaduje Visual Studio 2013 Update 3 nebo novější.  
    >   
    >  Přidání `/Zo` dojde k zakázání [upravit a pokračovat](../debugger/edit-and-continue-visual-csharp.md).  
  
   Když ladíte optimalizovaný kód, použijte **zpětný překlad** okně zobrazíte pokyny, které jsou ve skutečnosti vytvářejí a. Při nastavení zarážek, je potřeba vědět, že zarážka může být přesunout společně s instrukce. Zvažte například následující kód:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Předpokládejme, že jste nastavili zarážku na tomto řádku. Očekáváte zarážce 10krát, ale pokud je optimalizovaný kód, zarážka se projeví pouze jednou. Důvodem je, že první instrukce nastaví hodnotu `x` na hodnotu 0. Kompilátor rozpozná, že to jenom je třeba provést jednou a přesouvá ji ze smyčky. Zarážka se přesune s ním. Pokyny, které porovnání a zvýší `x` zůstávají uvnitř smyčky. Při prohlížení **zpětný překlad** okně [jednotku kroku](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) se automaticky nastaví na instrukci pro větší kontrolu, což je užitečné, když krokovat optimalizovaný kód.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)



