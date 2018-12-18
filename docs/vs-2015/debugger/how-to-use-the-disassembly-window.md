---
title: 'Postupy: použití okna zpětného překladu | Dokumentace Microsoftu'
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
manager: ghogen
ms.openlocfilehash: 67f9307f2f5fece64ee2ee11dd48863b9a951180
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760906"
---
# <a name="how-to-use-the-disassembly-window"></a>Postupy: Použití okna zpětného překladu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce je dostupná jenom v případě, že je povoleno ladění na úrovni adres **možnosti** dialogovém okně **ladění** uzlu. Není k dispozici pro ladění skriptu nebo SQL.  
  
 **Zpětný překlad** okno zobrazuje kódu sestavení odpovídajícího pokynů vytvořeným kompilátorem. Pokud ladíte spravovaný kód, tyto pokyny k sestavení odpovídají na nativní kód vytvořený kompilátorem Just-in-Time (JIT), ne Microsoft intermediate language (MSIL) generovaný kompilátorem Visual Studio.  
  
 Kromě pokyny sestavení **zpětný překlad** okna můžete zobrazit následující volitelné informace:  
  
- Adresa paměti, kde se nachází každou instrukci. Pro nativní aplikace Toto je skutečná adresa paměti. Visual Basic, C# nebo spravovaný kód je posun od začátku této funkce.  
  
- Zdrojový kód, ze kterého je odvozen kódu sestavení.  
  
- Kód bajtů – znázornění bajtu skutečný nebo instrukce jazyka MSIL.  
  
- Názvy symbolů pro adresy paměti.  
  
- Čísla řádků zdrojového kódu.  
  
  Instrukcí sestavení jazyka se skládají z klávesových zkratek, které jsou zkratky pro instrukcí názvy a symboly, které představují proměnné, registry a konstanty. Každou instrukci strojového jazyka je reprezentován symbolické jeden jazyk sestavení, obvykle následovaného jednou nebo více proměnných, registry nebo konstanty.  
  
  Pokud nelze číst jazyku sestavení a chcete využívat všech výhod v okně zpětný překlad, projděte si dobré adresáře na programovací jazyk sestavení. Jazyk sestavení programování je nad rámec co jsme adresy v tomto stručném úvodu v okně zpětný překlad.  
  
  Protože kód sestavení spoléhá na registrech procesoru, nebo v případě spravovaného kódu, registruje modul common language runtime, ale bude často užitečné použít okno zpětný překlad ve spojení s oknem registrů, které umožňuje zkoumat registru obsah.  
  
  Pravděpodobně se nikdy máte touha nebo potřebujete zobrazíte pokyny strojového kódu v jejich a číselné formuláře, nikoli jazyk sestavení. Ale pokud chcete udělat, je použití okna paměť pro tento účel nebo zvolte kód bajtů z místní nabídky v okně zpětný překlad.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Chcete-li zobrazit okno zpětného překladu  
  
-   Na **ladění** nabídce zvolte **Windows**a klikněte na tlačítko **zpětný překlad**.  
  
     Ladicí program musí být spuštěná nebo v režimu pozastavení.  
  
### <a name="to-turn-optional-information-on-or-off"></a>Chcete-li zapnout nebo vypnout volitelné informace  
  
-   Klikněte pravým tlačítkem myši **zpětný překlad** okna a nastavení nebo vymazat požadované možnosti v místní nabídce.  
  
     Žlutá šipka na levém okraji označuje umístění aktuální bod provádění. Pro nativní kód odpovídá čítač programu CPU. Toto umístění se zobrazí další instrukci, která se spustí ve svém programu.  
  
     Další informace najdete v tématu [stránkování nahoru nebo dolů v paměti](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Postupy: Použití okna Registry](../debugger/how-to-use-the-registers-window.md)





