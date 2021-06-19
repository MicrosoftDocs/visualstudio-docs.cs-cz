---
title: Ladění narušení přístupu v jazyce C++ | Microsoft Docs
description: Tipy k řešení potíží s porušením přístupu najdete v případě, že je kandidátem více než jeden ukazatel. Nedávné verze Visual Studio jako ukazatel na errant.
ms.custom: SEO-VS-2020
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3689942c9db9fde3598590cf30100fc590c50753
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387031"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Jak můžu ladit porušení přístupu C++?

## <a name="problem-description"></a>Popis problému

V mém programu dochází k narušení přístupu. Jak to můžu ladit?

## <a name="solution"></a>Řešení

Pokud dojde k narušení přístupu na řádku kódu, který přeskakuje více ukazatelů, může být obtížné zjistit, který ukazatel narušení přístupu způsobil. Počínaje Visual Studio 2015 Update 1 teď dialogové okno výjimky explicitně uvádí ukazatel, který způsobil narušení přístupu.

Například v případě následujícího kódu by mělo dojít k narušení přístupu:

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Pokud tento kód spustíte v Visual Studio 2015 Update 1, mělo by se zobrazit následující dialogové okno výjimky:

![Snímek obrazovky Microsoft Visual Studio výjimkami zobrazující porušení přístupu pro čtení pro A->B byl nullptr Je vybráno tlačítko Break (Přerušit).](../debugger/media/accessviolationcplus.png)

Pokud nemůžete určit, proč ukazatel způsobil narušení přístupu, proveďte trasování kódu a ujistěte se, že byl ukazatel způsobující problém přiřazen správně.  Pokud se předá jako parametr, ujistěte se, že je předán správně a že nechtěně nevytváříte [mělkou kopii](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Potom vytvořením datové zarážky pro sledovaný ukazatel ověřte, že se hodnoty neúmyslně nemění někde v programu, abyste se ujistili, že se neupravují jinde v programu. Další informace o datových zarážkách najdete v části datové zarážky v tématu [Použití zarážek](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)