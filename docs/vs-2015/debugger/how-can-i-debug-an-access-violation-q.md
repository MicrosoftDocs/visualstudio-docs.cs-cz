---
title: Jak mohu ladit narušení přístupu? | Dokumenty Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6188cc273cdea1755071e36f606fb8f041508d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297314"
---
# <a name="how-can-i-debug-an-access-violation"></a>Jak mohu ladit narušení přístupu?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Popis problému  
 Tento program vytvoří narušení přístupu. Jak to lze odladit?  
  
## <a name="solution"></a>Řešení  
 Pokud dojde k narušení přístupu na řádek kódu, který přistoupí přes většího počtu ukazatelů, může být obtížné zjistit, které ukazatel způsobil narušení přístupu. Od verze Visual Studio 2015 Update 1, dialogové okno výjimky nyní explicitně názvy ukazatel, který způsobil narušení přístupu.  
  
 Například směru následujícím kódem, měli byste získat narušení přístupu:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 Při spuštění tohoto kódu ve Visual Studio 2015 Update 1, byste měli vidět následující dialogové okno výjimky:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Pokud nelze určit, proč je ukazatel způsobil narušení přístupu, trasování skrze kód a ujistěte se, že ukazatel příčinou problému, má přiřazenou správně.  Pokud se předává jako parametr, ujistěte se, že je předaný správně, a Vy nechtěně nevytvoříte [kopii](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)s podmnožinou. Pak ověřte, že se hodnoty neúmyslně v programu nezměnily, vytvořením datové zarážky pro daný ukazatel, abyste se ujistili, že se nemění jinde v programu. Další informace o zarážekch dat naleznete v části datové zarážky v tématu [použití zarážek](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
