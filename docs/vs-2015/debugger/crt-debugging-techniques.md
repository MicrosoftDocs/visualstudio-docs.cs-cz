---
title: Techniky ladění CRT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a69defe75b80ef1f395931017dfc942398ca2710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161479"
---
# <a name="crt-debugging-techniques"></a>Techniky ladění CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud ladíte program, který používá knihovnu run-time jazyka C, mohou být tyto techniky ladění užitečné.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití knihovny ladění CRT](../debugger/crt-debug-library-use.md)  
 Popisuje podporu ladění, kterou poskytuje knihovna run-time jazyka C, a poskytuje pokyny pro přístup k nástrojům.  
  
 [Makra pro vytváření sestav](../debugger/macros-for-reporting.md)  
 Poskytuje informace o **_RPTn** a **_RPTFn** makrech (definovaných v souboru Crtdbg. H), které nahradí použití `printf` příkazů pro ladění.  
  
 [Ladění verzí funkcí přidělení haldy](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Tento článek popisuje speciální ladicí verze funkcí přidělení haldy, včetně: Jak volání map CRT nahlasují, jaké jsou výhody volání explicitně, jak vyhnout konverzi, sledovat samostatné typy přidělení v klientských blocích a výsledky nedefinovat _DEBUG.  
  
 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)  
 Poskytuje odkazy na správu paměti a haldu ladění, typy bloků v haldě ladění, použití haldy ladění, funkce vytváření sestav o stavu haldy a sledování požadavků na přidělení haldy.  
  
 [Zápis funkce háku ladění](../debugger/debug-hook-function-writing.md)  
 Obsahuje odkazy na funkce zavěšení bloků klienta, funkce zavěšení přidělení, zavěšení přidělení a přidělení paměti CRT a funkce zavěšení sestav.  
  
 [Hledání nevrácené paměti pomocí knihovny CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Zahrnuje techniky pro detekci a izolaci nevracení paměti pomocí ladicího programu a knihovny run-time jazyka C.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)  
 Popisuje některé běžné problémy s laděním a techniky pro aplikace v jazyce C a C++.  
  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)  
 Poskytuje doporučení pro bezpečnější ladění.
