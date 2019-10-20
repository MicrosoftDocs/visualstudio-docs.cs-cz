---
title: Spustit příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663497"
---
# <a name="start-command"></a>Spustit – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Začíná ladit spouštěný projekt.

## <a name="syntax"></a>Syntaxe

```
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
 `address` volitelné. Adresa, na které program pozastaví provádění, podobně jako zarážka ve zdrojovém kódu. Tento argument je platný pouze v režimu ladění.

## <a name="remarks"></a>Poznámky
 **Spouštěcí** příkaz po provedení provede operaci RunToCursor na zadané adrese.

## <a name="example"></a>Příklad
 Tento příklad spustí ladicí program a ignoruje všechny výjimky, ke kterým dojde.

```
>Debug.Start
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
