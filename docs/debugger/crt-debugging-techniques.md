---
title: Techniky ladění CRT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 890dec4a47a4dd49fa75521aaad068d331652a92
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458424"
---
# <a name="crt-debugging-techniques"></a>Techniky ladění CRT
Pokud ladíte program, který používá běhové knihovny jazyka C, může být užitečné tyto techniky ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití knihovny ladění CRT](../debugger/crt-debug-library-use.md)  
 Popisuje podporu ladění poskytované běhové knihovny jazyka C a poskytuje pokyny pro přístup k nástroje.  
  
 [Makra pro vytváření sestav](../debugger/macros-for-reporting.md)  
 Poskytuje informace o **_rptn –** a **_rptfn –** makra (definovanou v CRTDBG. H), který nahradí použití `printf` příkazy pro ladění.  
  
 [Ladění verzí funkcí přidělení haldy](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Popisuje speciální ladění verzí funkcí přidělení haldy, včetně: jak CRT mapuje volání, výhod volání je explicitně, jak se vyhnout převodu sledování samostatných typy přidělování v blocích klienta a výsledky nejsou definování _ LADĚNÍ.  
  
 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)  
 Obsahuje odkazy na Správa paměti a haldy ladění, typy bloků v haldě ladění pomocí haldy ladění, stavu haldy funkce vytváření sestav a sledování požadavků na přidělení haldy.  
  
 [Zápis funkce háku ladění](../debugger/debug-hook-function-writing.md)  
 Seznamy odkazy na klientský blok napojit funkce, funkce háku přidělení, háky přidělení a přidělení paměti CRT a funkce háku sestavy.  
  
 [Hledání nevrácené paměti pomocí knihovny CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Popisuje techniky pro zjištění a izolace nevracení paměti pomocí ladicího programu a běhové knihovny jazyka C.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)  
 Popisuje některé běžné problémy ladění a techniky pro C a C++ aplikace.  
  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)  
 Poskytuje doporučení pro bezpečnější ladění.