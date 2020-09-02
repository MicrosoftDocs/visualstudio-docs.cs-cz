---
title: 'Postupy: Ladění optimalizovaného kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 68ce036d420293e8a75bec1b2cac9f9ee8f8fcd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675615"
---
# <a name="how-to-debug-optimized-code"></a>Postupy: Ladění optimalizovaného kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
> Možnost kompilátoru [/Zo (vylepšit optimalizované ladění)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)(představená v aktualizaci Visual Studio Update 3) generuje bohatší informace ladění pro optimalizovaný kód (projekty, které nejsou sestavené pomocí možnosti kompilátoru **/od** . Viz [Možnosti/o (optimalizace kódu)](https://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)). To zahrnuje vylepšenou podporu pro ladění místních proměnných a vložené funkce.  
>   
> Možnost [Upravit a pokračovat](../debugger/edit-and-continue-visual-csharp.md) je zakázána při použití možnosti **/Zo** ocompiler.  
  
 Když kompilátor optimalizuje kód, přemístí a reorganizuje pokyny. Výsledkem je efektivnější zkompilovaný kód. Kvůli této změně uspořádání nemůže ladicí program vždy identifikovat zdrojový kód, který odpovídá sadě instrukcí.  
  
 Optimalizace může ovlivnit:  
  
- Místní proměnné, které lze odebrat optimalizátorem nebo přesunout do umístění, které ladicí program nerozumí.  
  
- Pozice uvnitř funkce, které se změní, když Optimalizátor slučuje bloky kódu.  
  
- Názvy funkcí pro rámce v zásobníku volání, které mohou být nesprávné, pokud Optimalizátor sloučí dvě funkce.  
  
  Rámce, které vidíte v zásobníku volání, jsou téměř vždy správné, ale za předpokladu, že máte symboly pro všechny snímky. Snímky v zásobníku volání budou nesprávné, pokud máte poškozený zásobník, pokud máte funkce napsané v jazyce sestavení nebo pokud existují snímky operačního systému bez odpovídajícího symbolu v zásobníku volání.  
  
  Globální a statické proměnné jsou vždy zobrazeny správně. Takže je rozložení struktury. Pokud máte ukazatel na strukturu a hodnota ukazatele je správná, zobrazí se v každé členské proměnné struktury správná hodnota.  
  
  Z důvodu těchto omezení byste měli ladit pomocí neoptimalizované verze programu, pokud je to možné. Ve výchozím nastavení je optimalizace vypnuta v konfiguraci ladění Visual C++ programu a je zapnutá v konfiguraci vydané verze.  
  
  Chyba se však může zobrazit pouze v optimalizované verzi programu. V takovém případě je nutné ladit optimalizovaný kód.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Zapnutí optimalizace v konfiguraci sestavení ladění  
  
1. Když vytvoříte nový projekt, vyberte `Win32 Debug` cíl. Použijte `Win32``Debug` cíl, dokud nebude program plně laděn a jste připraveni vytvořit `Win32 Release` cíl. Kompilátor neoptimalizuje `Win32 Debug` cíl.  
  
2. Vyberte projekt v Průzkumník řešení.  
  
3. V nabídce **zobrazení** klikněte na položku **stránky vlastností**.  
  
4. V dialogovém okně **stránky vlastností** se ujistěte, že `Debug` je vybrána možnost v rozevíracím seznamu **Konfigurace** .  
  
5. V zobrazení složky na levé straně vyberte složku **C/C++** .  
  
6. Ve složce **C++** vyberte `Optimization` .  
  
7. V seznamu vlastností vpravo Najděte `Optimization` . Nastavení vedle něj pravděpodobně říká `Disabled (` [/od](https://msdn.microsoft.com/library/b1ac31b7-e086-4eeb-be5e-488f7513f5f5) `)` . Vyberte jednu z dalších možností ( `Minimum Size``(` [/O1](https://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2) `)` , `Maximum Speed``(` [/O2](https://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2) `)` , `Full Optimization``(` [/Ox](https://msdn.microsoft.com/library/3ad7c30b-c615-428c-b1d0-2e024f81c760) `)` nebo `Custom` ).  
  
8. Pokud jste zvolili `Custom` možnost pro `Optimization` , můžete nyní nastavit možnosti pro kteroukoli z dalších vlastností, které jsou uvedeny v seznamu vlastností.  
  
9. Vyberte uzel vlastnosti konfigurace, C/C++, příkazový řádek stránky vlastností projektu a přidejte `(` [/Zo](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) `)` do textového pole **Další možnosti** .  
  
    > [!WARNING]
    > `/Zo` vyžaduje Visual Studio 2013 Update 3 nebo novější verzi.  
    >   
    >  Při přidání `/Zo` se zakáže [Úpravy a pokračování](../debugger/edit-and-continue-visual-csharp.md).  
  
   Při ladění optimalizovaného kódu použijte okno **zpětný překlad** k zobrazení pokynů, které jsou skutečně vytvořeny a provedeny. Při nastavování zarážek je nutné znát, zda se zarážka může pohybovat spolu s instrukcí. Zvažte například následující kód:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Předpokládejme, že jste na tomto řádku nastavili zarážku. Můžete očekávat, že zarážka bude dosaženo 10 krát, ale pokud je kód optimalizován, zarážka se narazí pouze jednou. Důvodem je, že první instrukce nastaví hodnotu `x` na 0. Kompilátor rozpozná, že je nutné provést pouze jednou a přesune ho mimo smyčku. Zarážka se přesune s ním. Pokyny, které porovnávají a zvyšovat, `x` zůstávají uvnitř smyčky. Když zobrazíte okno **zpětný překlad** , [jednotka kroku](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) je automaticky nastavena na instrukci pro větší kontrolu, což je užitečné při Krokovat s použitím optimalizovaného kódu.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
