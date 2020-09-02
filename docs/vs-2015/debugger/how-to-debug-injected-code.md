---
title: 'Postupy: ladění vloženého kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df35a25534961c6ab94891d2da6fe54f05c37a3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681080"
---
# <a name="how-to-debug-injected-code"></a>Postupy: Ladění vloženého kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Použití atributů může značně zjednodušit programování v jazyce C++. Další informace najdete v tématu [Koncepty](https://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Některé atributy jsou interpretovány přímo kompilátorem. Jiné atributy vloží kód do zdroje programu, který kompilátor potom zkompiluje. Tento vložený kód usnadňuje programování tím, že snižuje množství kódu, který musíte napsat. V některých případech ale může dojít k selhání vaší aplikace při provádění vloženého kódu. Pokud k tomu dojde, budete pravděpodobně chtít podívat se na vložený kód. Visual Studio nabízí dva způsoby, jak zobrazit vložený kód:  
  
- Vložený kód můžete zobrazit v okně **zpětný překlad** .  
  
- Pomocí [/FX](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560)můžete vytvořit sloučený zdrojový soubor, který obsahuje původní a vložený kód.  
  
  Okno zpětný **Překlad** zobrazuje instrukce pro jazyk sestavení, které odpovídají zdrojovému kódu, a kód vložený pomocí atributů. Kromě toho může okno zpětný **Překlad** zobrazit anotaci zdrojového kódu.  
  
### <a name="to-turn-on-source-annotation"></a>Zapnutí zdrojové poznámky  
  
- Klikněte pravým tlačítkem myši na okno **zpětný překlad** a v místní nabídce vyberte možnost **Zobrazit zdrojový kód** .  
  
     Pokud znáte umístění atributu v okně zdroje, můžete použít místní nabídku k vyhledání vloženého kódu v okně **zpětný překlad** .  
  
### <a name="to-view-injected-code"></a>Zobrazení vloženého kódu  
  
1. Ladicí program musí být v režimu přerušení.  
  
2. V okně zdrojového kódu umístěte kurzor před atribut, jehož vložený kód chcete zobrazit.  
  
3. Klikněte pravým tlačítkem a z místní nabídky vyberte **Přejít na zpětný překlad** .  
  
     Pokud se umístění atributu blíží aktuálnímu bodu spuštění, můžete vybrat okno **zpětný překlad** z nabídky **ladění** .  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Zobrazení kódu zpětného překladu v aktuálním bodu spuštění  
  
1. Ladicí program musí být v režimu přerušení.  
  
2. V nabídce **ladění** vyberte možnost **Windows**a klikněte na **zpětný překlad**.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
