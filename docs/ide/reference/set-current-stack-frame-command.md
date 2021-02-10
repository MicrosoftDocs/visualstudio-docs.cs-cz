---
title: Nastavit aktuální rámec zásobníku – příkaz
description: Přečtěte si o příkazu nastavit aktuální rámec zásobníku a o tom, jak vám umožní nastavit konkrétní rámec zásobníku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1c8d0ade87ee7759593c8a465b43439f71d50d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957748"
---
# <a name="set-current-stack-frame-command"></a>Nastavit aktuální rámec zásobníku – příkaz
Umožňuje nastavit konkrétní rámec zásobníku.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumenty
`index`

Povinná hodnota. Vybere rámec zásobníku podle jeho indexu.

## <a name="example"></a>Příklad

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)