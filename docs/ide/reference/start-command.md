---
title: Spustit – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 946c4e39b48d15352ef5fa8ae240fb3fe9da5b9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645240"
---
# <a name="start-command"></a>Spustit – příkaz
Začíná ladit spouštěný projekt.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
`address`

Volitelné. Adresa, na které program pozastaví provádění, podobně jako zarážka ve zdrojovém kódu. Tento argument je platný pouze v režimu ladění.

## <a name="remarks"></a>Poznámky
**Spouštěcí** příkaz po provedení provede operaci RunToCursor na zadané adrese.

## <a name="example"></a>Příklad
Tento příklad spustí ladicí program a ignoruje všechny výjimky, ke kterým dojde.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)