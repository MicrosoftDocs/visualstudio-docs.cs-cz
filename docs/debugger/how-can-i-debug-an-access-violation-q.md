---
title: Ladění narušení C++ přístupu | Microsoft Docs
ms.custom: seodec18
ms.date: 02/05/2019
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f0235cc00a740069a77afd492cd585788ea666d2
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911465"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Jak mohu ladit narušení C++ přístupu?

## <a name="problem-description"></a>Popis problému

Program vytvoří porušení přístupu. Jak se dá ladit?

## <a name="solution"></a>Řešení

Pokud dojde k narušení přístupu na řádku kódu, který odkazuje na více ukazatelů, může být obtížné zjistit, který ukazatel způsobil narušení přístupu. Počínaje verzí Visual Studio 2015 Update 1 se v dialogovém okně výjimka teď explicitně pojmenuje ukazatel, který způsobil narušení přístupu.

Například s ohledem na následující kód byste měli mít porušení přístupu:

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

Pokud spustíte tento kód v aplikaci Visual Studio 2015 Update 1, mělo by se zobrazit následující dialog výjimky:

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

Pokud nemůžete určit, proč ukazatel způsobil narušení přístupu, Sledujte kód, abyste se ujistili, že ukazatel způsobující problém byl správně přiřazen.  Pokud se předává jako parametr, ujistěte se, že je předaný správně, a Vy nechtěně nevytvoříte [kopii](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)s podmnožinou. Pak ověřte, že se hodnoty neúmyslně v programu nezměnily, vytvořením datové zarážky pro daný ukazatel, abyste se ujistili, že se nemění jinde v programu. Další informace o zarážekch dat naleznete v části datové zarážky v tématu [použití zarážek](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Viz také:
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)