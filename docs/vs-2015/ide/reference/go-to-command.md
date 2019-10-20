---
title: Přejít na příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661206"
---
# <a name="go-to-command"></a>Přejít na – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přesune kurzor na zadaný řádek.

## <a name="syntax"></a>Syntaxe

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
 `linenumber` volitelné. Celé číslo představující číslo řádku, na který se má přejít

## <a name="remarks"></a>Poznámky
 Číslování řádků začíná na jednom. Pokud je hodnota `linenumber` menší než jedna, zobrazí se první řádek. Pokud je hodnota `linenumber` větší než číslo posledního řádku, zobrazí se poslední řádek.

 Pokud není zadána hodnota `linenumber`, zobrazí se dialogové okno **Přejít na řádek** .

 Alias pro tento příkaz je GoToLn.

## <a name="example"></a>Příklad

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
