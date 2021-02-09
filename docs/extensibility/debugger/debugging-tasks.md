---
title: Úlohy ladění | Microsoft Docs
description: Seznamte se s úkoly potřebnými k ladění programu, jako je například připojení k ladicímu stroji, generování spouštěcích událostí a zarážky se zarážkami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f27bc3f261e66791f41034923989b2cd61e09db6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904760"
---
# <a name="debug-tasks"></a>Úlohy ladění
Chcete-li ladit program, musí být spuštěn a k němu musí být připojen ladicí stroj (DE), nebo jinak musí být k dříve spuštěnému programu připojen příkaz DE. Po připojení musí DE vygenerovat určité události spuštění. V reakci se ladicí balíček pokusí vázat zarážky nastavené v integrovaném vývojovém prostředí (IDE). Když program narazí na vázanou zarážku, zastaví a počká na vstup uživatele.

## <a name="in-this-section"></a>V této části
 [Problémy se zabezpečením](../../extensibility/debugger/security-issues.md) Popisuje kroky zabezpečení, které jsou nutné k ladění programu.

 [Spustit program](../../extensibility/debugger/launching-a-program.md) Poskytuje podrobné pokyny, jak zadat DE, který volá operační systém pro spuštění programu.

 [Připojit přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md) Popisuje proces, který se používá k ladění programu v procesu, který je už spuštěný.

 [Po spuštění Odeslat události po spuštění](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Zobrazuje události, které se provádějí po připojení DE k programu, dokud je program v jeho hlavním vstupním bodě a připravený k ladění.

 [Řízení provádění](../../extensibility/debugger/control-of-execution.md) Vysvětluje, jak obvykle pošle událost vstupního bodu, událost dokončení načtení nebo událost zastavení v závislosti na okolnostech.

 [Vázání zarážek](../../extensibility/debugger/binding-breakpoints.md) Popisuje, jak, pokud uživatel nastaví zarážku, rozhraní IDE formuluje požadavek a vyzve relaci ladění, aby vytvořila zarážku.

 [Výrazy vyhodnocení](../../extensibility/debugger/evaluating-expressions.md) Vysvětluje, jak se vytvářejí výrazy a co se stane, když se vyhodnotí výraz.

 [Vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md) Vysvětluje, jakým způsobem vyhodnocovací filtr výrazů (EE) podporuje typy vizualizace a vlastní prohlížeče.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní koncepty architektury ladění.

 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md) Poskytuje přehled komponent ladění sady Visual Studio, které zahrnují popisovač DE, EE a symbol (SH).

 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak DE funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

## <a name="see-also"></a>Viz také
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
