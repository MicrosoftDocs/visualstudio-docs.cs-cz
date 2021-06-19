---
title: Zjistit, jestli moje ukazatele poškodily adresu paměti | Microsoft Docs
description: Chcete-li zjistit, zda je ukazatel poškozen pamětí, můžete vyhledat poškození haldy a můžete nastavit zarážku dat a zjistit, jak je upravena hodnota.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 836cc0363da0e20c45d83e1b2c13081e480fa919
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386966"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak zjistím, že moje ukazatele poškodily adresu paměti?
## <a name="problem-description"></a>Popis problému
 Myslím, že jeden z mých ukazatelů může poškodit paměť na adrese 0x00408000. Jak můžu zjistit, co se děje?

## <a name="solution"></a>Řešení

#### <a name="check-for-heap-corruption"></a>Kontrolovat poškození haldy

- Většina poškození paměti je způsobená poškozením haldy. Zkuste použít nástroj Global Flags (gflags.exe) nebo pageheap.exe. Viz [/Windows-hardware/Drivers/Debugger/Gflags-and-PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Zjištění, kde je adresa paměti upravena

1. Nastavte zarážku dat na 0x00408000. Viz [Nastavení zarážky změny dat (pouze nativní C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Při dosažení zarážky použijte okno **paměť** k zobrazení obsahu paměti od 0x00408000. Další informace najdete v tématu [paměťová okna](../debugger/memory-windows.md).

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
