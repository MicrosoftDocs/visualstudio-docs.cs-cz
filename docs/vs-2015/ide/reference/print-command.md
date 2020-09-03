---
title: Tisk příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662155"
---
# <a name="print-command"></a>Tisk – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyhodnotí výraz nebo zobrazí zadaný text.

## <a name="syntax"></a>Syntaxe

```
Debug.Print text
```

## <a name="arguments"></a>Argumenty
 `text` Požadovanou. Výraz, který se má vyhodnotit, nebo text, který se má zobrazit

## <a name="remarks"></a>Poznámky
 Jako alias pro tento příkaz můžete použít otazník (?). Například příkaz

```
>Debug.Print expA
```

 lze také zapsat

```
>? expA
```

 Obě verze tohoto příkazu vrátí aktuální hodnotu výrazu `expA` .

## <a name="example"></a>Příklad

```
>Debug.Print varA
```

## <a name="see-also"></a>Viz také
 [Evaluate – příkaz příkazu](../../ide/reference/evaluate-statement-command.md) příkazového [řádku pro](../../ide/reference/command-window.md) [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md) [Najít nebo příkaz zadejte](../../ide/find-command-box.md) [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
