---
title: Jak zjistím, že moje ukazatele poškodily adresu paměti? | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d4f23b885b2e72e53d288946df18e038d9d956d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476771"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak zjistím, že moje ukazatele poškodily adresu paměti?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Popis problému  
 Myslím, že jeden z mých ukazatelů může poškodit paměť na adrese 0x00408000. Jak můžu zjistit, co se děje?  
  
## <a name="solution"></a>Řešení  
  
#### <a name="check-for-heap-corruption"></a>Kontrolovat poškození haldy  
  
- Většina poškození paměti je způsobená poškozením haldy. Zkuste použít nástroj Global Flags (gflags.exe) nebo pageheap.exe. Viz [Gflags a PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap) a [Jak používat nástroj Pageheap k detekci chyb paměti v Microsoft Visual C++ projektu](https://support.microsoft.com/help/264471/how-to-use-the-pageheap-utility-to-detect-memory-errors-in-a-microsoft).
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Zjištění, kde je adresa paměti upravena  
  
1. Nastavte zarážku dat na 0x00408000. Viz [Nastavení zarážky změny dat (pouze nativní C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2. Při dosažení zarážky použijte okno **paměť** k zobrazení obsahu paměti od 0x00408000. Další informace najdete v tématu [paměťová okna](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
