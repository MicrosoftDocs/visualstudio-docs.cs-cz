---
title: 'Postupy: použití okna zpětného překladu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c25c3cdeb96abacb4123b2d0a851ac3d4acb0cd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696143"
---
# <a name="how-to-use-the-disassembly-window"></a>Postupy: Použití okna zpětného překladu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce je k dispozici pouze v případě, že je povoleno ladění na úrovni adres v dialogovém okně **Možnosti** , uzel **ladění** . Není k dispozici pro ladění skriptů nebo SQL.  
  
 Okno zpětný **Překlad** zobrazuje kód sestavení odpovídající pokynům vytvořeným kompilátorem. Pokud ladíte spravovaný kód, tyto pokyny k sestavení odpovídají nativnímu kódu vytvořenému kompilátorem JIT (just-in-time), nikoli pomocí jazyka MSIL (Microsoft Intermediate Language) vygenerovaného kompilátorem sady Visual Studio.  
  
 Kromě pokynů k sestavení může okno **zpětný překlad** zobrazit následující volitelné informace:  
  
- Adresa paměti, kde se nachází každá instrukce. Pro nativní aplikace se jedná o skutečnou adresu paměti. U Visual Basic, C# nebo spravovaného kódu se jedná o posun od začátku funkce.  
  
- Zdrojový kód, ze kterého je odvozen kód sestavení.  
  
- Bajty kódu – Byte reprezentace skutečných instrukcí počítače nebo MSIL.  
  
- Názvy symbolů pro paměťové adresy.  
  
- Čísla řádků odpovídající zdrojovému kódu.  
  
  Instrukce pro sestavení jazyka se skládají z klávesových zkratek, které jsou zkratkami pro názvy instrukcí a symboly, které představují proměnné, Registry a konstanty. Jednotlivé instrukce v jazyce počítače jsou reprezentovány jedním z jazykových instrukcí pro sestavení, obvykle následovány jednou nebo více proměnnými, registry nebo konstantami.  
  
  Pokud nemůžete číst jazyk sestavení a chcete plně využít výhod okna zpětný překlad, prostudujte si dobrou příručku o programování sestavení jazyka. Programování sestavení jazyka je nad rámec toho, co můžeme v tomto stručném úvodu do okna zpětného překladu vyřešit.  
  
  Vzhledem k tomu, že kód sestavení spoléhá silně na Registry procesorů nebo v případě spravovaného kódu, registrů modulu CLR (Common Language Runtime) často zjistíte, že je vhodné použít okno zpětný překlad ve spojení s oknem Registry, což vám umožňuje kontrolovat obsah registru.  
  
  Pravděpodobně nikdy nebudete mít potřebná přání ani nebude nutné zobrazovat instrukce strojového kódu v nezpracovaném číselném tvaru, nikoli v jazyku sestavení. Nicméně pokud to chcete udělat, můžete použít okno paměti pro tento účel nebo zvolit bajty kódu z místní nabídky v okně zpětný překlad.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Zobrazení okna zpětný překlad  
  
- V nabídce **ladění** vyberte možnost **Windows**a klikněte na **zpětný překlad**.  
  
     Ladicí program musí být spuštěný nebo v režimu přerušení.  
  
### <a name="to-turn-optional-information-on-or-off"></a>Zapnutí nebo vypnutí volitelných informací  
  
- Klikněte pravým tlačítkem myši na okno zpětného **překladu** a v místní nabídce nastavte nebo zrušte zaškrtnutí požadovaných možností.  
  
     Žlutá šipka na levém okraji označuje umístění aktuálního bodu spuštění. U nativního kódu to odpovídá čítači programu CPU. Toto umístění ukazuje další instrukci, která se spustí v programu.  
  
     Další informace najdete v části o [stránkování nahoru nebo dolů v paměti](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Postupy: Použití okna Registry](../debugger/how-to-use-the-registers-window.md)
