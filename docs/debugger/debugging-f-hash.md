---
title: 'Ladění F # | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b3bb2a9379dd6cd43bb0398ccda2b031b96d56e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473787"
---
# <a name="debugging-f"></a>Ladění F#
Ladění F # je podobná ladění žádný spravovaný jazyk s několika výjimkami:  
  
-   **Automobily** okno nezobrazí F # proměnné.  
  
-   Upravit a pokračovat není podporována pro F #. Úpravy během relace ladění F # – kód je možné, ale je nutno. Vzhledem k tomu, že během ladicí relace se nepoužijí změny kódu, úpravy F # kódu během ladění způsobí neshodu mezi zdrojový kód a kód laděné.  
  
-   Ladicí program nemůže rozpoznat F # výrazy. Zadání výrazu, v okně ladicí program nebo dialogové okno během ladění F #, musí překládat výraz do jazyka C# – syntaxe. Pokud jste přeložit výraz F # do jazyka C#, nezapomeňte mějte na paměti, že C# používá == jako jeden = používá relační operátor rovnosti a že F #.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
