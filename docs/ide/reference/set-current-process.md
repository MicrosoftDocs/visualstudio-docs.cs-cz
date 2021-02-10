---
title: Nastavit aktuální proces
description: Přečtěte si o příkazu nastavit aktuální proces a o tom, jak nastaví zadaný proces jako aktivní proces v ladicím programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef9475e9336acd5c10cee604d453706ea7321c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957800"
---
# <a name="set-current-process"></a>Nastavit aktuální proces
Nastaví zadaný proces jako aktivní proces v ladicím programu.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
`index`

Povinná hodnota. Index procesu.

## <a name="remarks"></a>Poznámky
Můžete se připojit k více procesům při ladění, ale v Dubber je v daném okamžiku aktivní pouze jeden proces. Pomocí `SetCurrentProcess` příkazu můžete nastavit aktivní proces.

## <a name="example"></a>Příklad

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
