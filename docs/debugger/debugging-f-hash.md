---
title: 'Ladění F # | Microsoft Docs'
description: 'Projděte si seznam rozdílů mezi laděním F # v porovnání s laděním jiných spravovaných jazyků v aplikaci Visual Studio.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d2fed2765d04fa55c790afb7251a24b98a4d74f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872622"
---
# <a name="debugging-f"></a>Ladění F\#
Ladění F # je podobné ladění libovolného spravovaného jazyka, s několika výjimkami:

- Okno **Automatické** hodnoty nezobrazí proměnné F #.

- V jazyce F # není podporována úprava a pokračování. Úprava kódu F # během relace ladění je možná, ale měla by se jim vyhýbat. Vzhledem k tomu, že změny kódu nejsou během relace ladění aplikovány, úprava kódu F # během ladění způsobí neshodu mezi zdrojovým kódem a laděným kódem.

- Ladicí program nerozpozná výrazy F #. Chcete-li zadat výraz v okně ladicího programu nebo dialogové okno během ladění F #, je nutné výraz přeložit do syntaxe jazyka C#. Při překladu výrazu F # do jazyka C# nezapomeňte zapamatovat, že jazyk C# používá = = jako operátor porovnání pro rovnost a že F # používá jeden =.

## <a name="see-also"></a>Viz také
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
