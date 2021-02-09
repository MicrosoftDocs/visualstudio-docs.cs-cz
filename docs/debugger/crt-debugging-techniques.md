---
title: Techniky ladění CRT | Microsoft Docs
description: Existují různé techniky, pomocí kterých můžete ladit program, který používá knihovnu runtime jazyka C (CRT). V tomto článku a na jeho odkazech se dozvíte, jak tyto techniky využít.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d5f85584403cc18cd00708a8d4698723d614ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857607"
---
# <a name="crt-debugging-techniques"></a>Techniky ladění CRT
Pokud ladíte program, který používá knihovnu run-time jazyka C, mohou být tyto techniky ladění užitečné.

## <a name="in-this-section"></a>V tomto oddílu
 [Použití knihovny ladění CRT](../debugger/crt-debug-library-use.md)

 Popisuje podporu ladění poskytovanou knihovnou Run-Time jazyka C a poskytuje pokyny pro přístup k nástrojům.

 [Makra pro vytváření sestav](../debugger/macros-for-reporting.md)

 Poskytuje informace o **_RPTn** a **_RPTFn** makrech (definovaných v souboru Crtdbg. H), které nahradí použití `printf` příkazů pro ladění.

 [Ladění verzí funkcí přidělení haldy](../debugger/debug-versions-of-heap-allocation-functions.md)

 Tento článek popisuje speciální ladicí verze funkcí přidělení haldy, včetně: Jak volání map CRT nahlasují, jaké jsou výhody volání explicitně, jak vyhnout konverzi, sledovat samostatné typy přidělení v klientských blocích a výsledky nedefinovat _DEBUG.

 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)

 Poskytuje odkazy na správu paměti a haldu ladění, typy bloků v haldě ladění, použití haldy ladění, funkce vytváření sestav o stavu haldy a sledování požadavků na přidělení haldy.

 [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)

 Obsahuje odkazy na funkce zavěšení bloků klienta, funkce zavěšení přidělení, zavěšení přidělení a přidělení paměti CRT a funkce zavěšení sestav.

 [Hledání nevrácené paměti pomocí knihovny CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)

 Zahrnuje techniky pro detekci a izolaci nevracení paměti pomocí ladicího programu a knihovny jazyka C Run-Time.

## <a name="related-sections"></a>Související oddíly

- [Ladění nativního kódu](../debugger/debugging-native-code.md) – popisuje některé běžné problémy s laděním a techniky pro aplikace v jazyce C a C++.
- [Zabezpečení ladicího programu](../debugger/debugger-security.md) – poskytuje doporučení pro bezpečnější ladění.