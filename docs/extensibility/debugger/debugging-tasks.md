---
title: Ladění úkolů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738956"
---
# <a name="debug-tasks"></a>Ladění úkolů
Chcete-li ladit program, musí být spuštěn a ladicí modul (DE) musí být připojen k němu, jinak DE musí být připojen k dříve spuštěný program. Po připojení musí DE generovat určité události při spuštění. V reakci na to se ladicí balíček pokusí svázat zarážky nastavené v ide. Když program narazí na vázanou zarážku, zastaví se a čeká na vstup uživatele.

## <a name="in-this-section"></a>V tomto oddílu
 [Problémy se zabezpečením](../../extensibility/debugger/security-issues.md) Popisuje kroky zabezpečení, které jsou potřebné k ladění programu.

 [Spuštění programu](../../extensibility/debugger/launching-a-program.md) Obsahuje podrobné pokyny k zadání de, který volá operační systém ke spuštění programu.

 [Připojení přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md) Popisuje proces používaný k ladění programu v procesu, který je již spuštěn.

 [Odeslání událostí spuštění po spuštění](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Uvádí události, ke kterým dochází po připojení DE k programu, dokud program není v hlavním vstupním bodě a je připraven k ladění.

 [Řízení provádění](../../extensibility/debugger/control-of-execution.md) Vysvětluje, jak DE obvykle odešle událost vstupního bodu, událost dokončení zatížení nebo událost zastavení v závislosti na okolnostech.

 [Zarážky vazby](../../extensibility/debugger/binding-breakpoints.md) Popisuje, jak, pokud uživatel nastaví zarážku, ide formuluje požadavek a vyzve relaci ladění k vytvoření zarážky.

 [Vyhodnocení výrazů](../../extensibility/debugger/evaluating-expressions.md) Vysvětluje, jak jsou vytvářeny výrazy a co se stane při vyhodnocení výrazu.

 [Vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md) Vysvětluje, jak jsou vizualizéry typu a vlastní prohlížeče podporovány vyhodnocením výrazu (EE).

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní ladění architektonických konceptů.

 [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md) Obsahuje přehled součástí ladění sady Visual Studio, které zahrnují obslužnou rutinu DE, EE a symbol (SH).

 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak DE pracuje současně v rámci kontextu kódování kódu, dokumentace a výrazu. Popisuje pro každý ze tří kontextů umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

## <a name="see-also"></a>Viz také
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
