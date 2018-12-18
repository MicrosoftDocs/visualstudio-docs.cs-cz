---
title: 'Postupy: ladění vloženého kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8efcc5780b27967644330e55dc540333a19105a2
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389335"
---
# <a name="how-to-debug-injected-code"></a>Postupy: Ladění vloženého kódu

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

Pomocí atributů může výrazně zjednodušit programování C++. Další informace najdete v tématu [koncepty](/cpp/windows/attributed-programming-concepts). Některé atributy jsou interpretovány kompilátorem přímo. Ostatní atributy vloží kód do zdroje program, který kompilátor pak zkompiluje. Tato vloženého kódu díky programování usnadnit tím, že snižuje množství kódu, který musíte napsat. V některých případech však chyba může způsobit selhání při provádění vloženého kódu aplikace. Pokud k tomu dojde, budete pravděpodobně chtít podívat na vložený kód. Visual Studio poskytuje dva způsoby, jak vidíte vloženého kódu:

- Můžete zobrazit kódu injektovaného do **zpětný překlad** okna.

- Pomocí [/Fx](/cpp/build/reference/fx-merge-injected-code), můžete vytvořit sloučené zdrojový soubor, který obsahuje původní a vloženého kódu.

**Zpětný překlad** okno zobrazuje instrukcí sestavení jazyka, které odpovídají zdrojový kód a kód vložený atributy. Kromě toho **zpětný překlad** okna můžete zobrazit poznámky zdrojového kódu.

## <a name="to-turn-on-source-annotation"></a>Chcete-li ve zdrojové poznámky

-   Klikněte pravým tlačítkem myši **zpětný překlad** okna a zvolte **zobrazit zdrojový kód** z místní nabídky.

     Pokud znáte umístění atributu v okně zdroje, můžete použít nabídku k vyhledání kódu injektovaného do **zpětný překlad** okna.

## <a name="to-view-injected-code"></a>Chcete-li zobrazit vloženého kódu

1.  Ladicí program musí být v režimu přerušení.

2.  V okně zdrojového kódu umístěte kurzor na slovo před atribut, jehož vloženého kódu, které chcete zobrazit.

3.  Klikněte pravým tlačítkem a vyberte **přejít na zpětný překlad** z místní nabídky.

     Pokud je atribut umístění u aktuální bod provádění, můžete vybrat **zpětný překlad** okna **ladění** nabídky.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Chcete-li zobrazit zpětný překlad kódu v aktuální bod provádění

1.  Ladicí program musí být v režimu přerušení.

2.  Z **ladění** nabídce zvolte **Windows**a klikněte na tlačítko **zpětný překlad**.

## <a name="see-also"></a>Viz také:

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)