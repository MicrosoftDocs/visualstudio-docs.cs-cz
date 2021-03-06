---
title: Spustit – příkaz
description: Přečtěte si o příkazu Start a o tom, jak začíná ladit spouštěný projekt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cae9d4630a854bc24c952380a1e27cbab42d261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938652"
---
# <a name="start-command"></a>Spustit – příkaz
Začíná ladit spouštěný projekt.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumenty
`address`

Nepovinný parametr. Adresa, na které program pozastaví provádění, podobně jako zarážka ve zdrojovém kódu. Tento argument je platný pouze v režimu ladění.

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
