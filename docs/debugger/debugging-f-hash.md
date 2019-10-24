---
title: Ladění F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7bc3934136f0966439bec2e4368488e52099602
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738271"
---
# <a name="debugging-f"></a>Ladění F \#
Ladění F# je podobné ladění libovolného spravovaného jazyka, s několika výjimkami:

- Okno **Automatické** hodnoty nezobrazuje F# proměnné.

- Úpravy a pokračování nejsou podporovány pro F#. Úpravy F# kódu během relace ladění jsou možné, ale je třeba se jim vyhnout. Vzhledem k tomu, že změny kódu nejsou během relace ladění aplikovány, úprava F# kódu během ladění způsobí neshodu mezi zdrojovým kódem a laděným kódem.

- Ladicí program nerozeznává F# výrazy. Chcete-li zadat výraz v okně ladicího programu nebo dialogové okno F# během ladění, je nutné výraz přeložit do C# syntaxe. Při překladu F# výrazu do C#nezapomeňte pamatovat, že C# používá = = jako operátor porovnání pro rovnost a který F# používá jeden =.

## <a name="see-also"></a>Viz také:
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
