---
title: 'Postupy: ladění vloženého kódu | Dokumentace Microsoftu'
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
manager: ghogen
ms.openlocfilehash: 7ff81b082c877098acec78e56ef9ef211cae8854
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778147"
---
# <a name="how-to-debug-injected-code"></a>Postupy: Ladění vloženého kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

POZNÁMKA:]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pomocí atributů může výrazně zjednodušit programování C++. Další informace najdete v tématu [koncepty](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Některé atributy jsou interpretovány kompilátorem přímo. Ostatní atributy vloží kód do zdroje program, který kompilátor pak zkompiluje. Tato vloženého kódu díky programování usnadnit tím, že snižuje množství kódu, který musíte napsat. V některých případech však chyba může způsobit selhání při provádění vloženého kódu aplikace. Pokud k tomu dojde, budete pravděpodobně chtít podívat na vložený kód. Visual Studio poskytuje dva způsoby, jak vidíte vloženého kódu:  
  
- Můžete zobrazit kódu injektovaného do **zpětný překlad** okna.  
  
- Pomocí [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), můžete vytvořit sloučené zdrojový soubor, který obsahuje původní a vloženého kódu.  
  
  **Zpětný překlad** okno zobrazuje instrukcí sestavení jazyka, které odpovídají zdrojový kód a kód vložený atributy. Kromě toho **zpětný překlad** okna můžete zobrazit poznámky zdrojového kódu.  
  
### <a name="to-turn-on-source-annotation"></a>Chcete-li ve zdrojové poznámky  
  
-   Klikněte pravým tlačítkem myši **zpětný překlad** okna a zvolte **zobrazit zdrojový kód** z místní nabídky.  
  
     Pokud znáte umístění atributu v okně zdroje, můžete použít nabídku k vyhledání kódu injektovaného do **zpětný překlad** okna.  
  
### <a name="to-view-injected-code"></a>Chcete-li zobrazit vloženého kódu  
  
1.  Ladicí program musí být v režimu přerušení.  
  
2.  V okně zdrojového kódu umístěte kurzor na slovo před atribut, jehož vloženého kódu, které chcete zobrazit.  
  
3.  Klikněte pravým tlačítkem a vyberte **přejít na zpětný překlad** z místní nabídky.  
  
     Pokud je atribut umístění u aktuální bod provádění, můžete vybrat **zpětný překlad** okna **ladění** nabídky.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Chcete-li zobrazit zpětný překlad kódu v aktuální bod provádění  
  
1.  Ladicí program musí být v režimu přerušení.  
  
2.  Z **ladění** nabídce zvolte **Windows**a klikněte na tlačítko **zpětný překlad**.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)



