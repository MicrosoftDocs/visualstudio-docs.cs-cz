---
title: Postup ladění vloženého kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a63a593a907908205d6724f3faf2c06d405bf0e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350040"
---
# <a name="how-to-debug-injected-code"></a>Postupy: Ladění vloženého kódu

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

Použití atributů může značně zjednodušit programování v jazyce C++. Další informace najdete v tématu [Koncepty](/cpp/windows/attributed-programming-concepts). Některé atributy jsou interpretovány přímo kompilátorem. Jiné atributy vloží kód do zdroje programu, který kompilátor potom zkompiluje. Tento vložený kód usnadňuje programování tím, že snižuje množství kódu, který musíte napsat. V některých případech ale může dojít k selhání vaší aplikace při provádění vloženého kódu. Pokud k tomu dojde, budete pravděpodobně chtít podívat se na vložený kód. Visual Studio nabízí dva způsoby, jak zobrazit vložený kód:

- Vložený kód můžete zobrazit v okně **zpětný překlad** .

- Pomocí [/FX](/cpp/build/reference/fx-merge-injected-code)můžete vytvořit sloučený zdrojový soubor, který obsahuje původní a vložený kód.

Okno zpětný **Překlad** zobrazuje instrukce pro jazyk sestavení, které odpovídají zdrojovému kódu, a kód vložený pomocí atributů. Kromě toho může okno zpětný **Překlad** zobrazit anotaci zdrojového kódu.

## <a name="to-turn-on-source-annotation"></a>Zapnutí zdrojové poznámky

- Klikněte pravým tlačítkem myši na okno **zpětný překlad** a v místní nabídce vyberte možnost **Zobrazit zdrojový kód** .

     Pokud znáte umístění atributu v okně zdroje, můžete použít místní nabídku k vyhledání vloženého kódu v okně **zpětný překlad** .

## <a name="to-view-injected-code"></a>Zobrazení vloženého kódu

1. Ladicí program musí být v režimu přerušení.

2. V okně zdrojového kódu umístěte kurzor před atribut, jehož vložený kód chcete zobrazit.

3. Klikněte pravým tlačítkem a z místní nabídky vyberte **Přejít na zpětný překlad** .

     Pokud se umístění atributu blíží aktuálnímu bodu spuštění, můžete vybrat okno **zpětný překlad** z nabídky **ladění** .

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Zobrazení kódu zpětného překladu v aktuálním bodu spuštění

1. Ladicí program musí být v režimu přerušení.

2. V nabídce **ladění** vyberte možnost **Windows**a klikněte na **zpětný překlad**.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)