---
title: Nastavit aktuální vlákno – příkaz
description: Přečtěte si o příkazu nastavit aktuální vlákno a o tom, jak nastaví zadané vlákno jako aktuální vlákno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cb58bf8751eb4299ecede18bac83770c3a7df96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957735"
---
# <a name="set-current-thread-command"></a>Nastavit aktuální vlákno – příkaz
Nastaví zadané vlákno jako aktuální vlákno.

## <a name="syntax"></a>Syntaxe

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argumenty
`index`

Povinná hodnota. Vybere vlákno podle jeho indexu.

## <a name="example"></a>Příklad

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)