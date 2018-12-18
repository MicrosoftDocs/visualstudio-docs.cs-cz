---
title: Techniky ladění CRT | Dokumentace Microsoftu
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
manager: ghogen
ms.openlocfilehash: 6745a31dcb7c37d12551248473b072d440116501
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801027"
---
# <a name="crt-debugging-techniques"></a>Techniky ladění CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud ladíte program, který používá knihovny run-time jazyka C, může být užitečné tyto techniky ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití knihovny ladění CRT](../debugger/crt-debug-library-use.md)  
 Popisuje podporu ladění poskytovaných knihovnou Run-Time jazyka C a poskytuje pokyny pro přístup k nástroji.  
  
 [Makra pro vytváření sestav](../debugger/macros-for-reporting.md)  
 Poskytuje informace o **_RPTn** a **_RPTFn** makra (definovaná v CRTDBG. H), který nahradí použití `printf` příkazy pro ladění.  
  
 [Ladění verzí funkcí přidělení haldy](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Tento článek popisuje zvláštní ladění verzí funkcí přidělení haldy, včetně: jak CRT mapuje volání, výhody volání je explicitně, jak se vyhnout převod sledování samostatné typy přidělení v blocích klienta a výsledky není definování _ LADĚNÍ.  
  
 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)  
 Obsahuje odkazy na správu paměti a halda ladění, typy bloků na haldě ladění pomocí haldy ladění, stavu haldy funkce generování sestav a sledování požadavků na přidělení haldy.  
  
 [Zápis funkce volání pro ladění](../debugger/debug-hook-function-writing.md)  
 Seznamy odkazů na klientský blok integrovat funkce, funkce háku přidělení, háky přidělení a přidělení paměti CRT a funkce háku sestavy.  
  
 [Hledání nevrácené paměti pomocí knihovny CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Popisuje postupy pro zjištění a izolace nevrácené paměti pomocí ladicího programu a knihovny jazyka C Run-Time.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)  
 Tento článek popisuje některé běžné problémy ladění a techniky pro aplikace C a C++.  
  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)  
 Poskytuje doporučení pro zabezpečení ladění.



