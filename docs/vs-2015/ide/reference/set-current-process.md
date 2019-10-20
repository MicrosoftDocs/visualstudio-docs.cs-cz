---
title: Nastavit aktuální proces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665470"
---
# <a name="set-current-process"></a>Nastavit aktuální proces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví zadaný proces jako aktivní proces v ladicím programu.

## <a name="syntax"></a>Syntaxe

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
 `index` nutné. Index procesu.

## <a name="remarks"></a>Poznámky
 Můžete se připojit k více procesům při ladění, ale v Dubber je v daném okamžiku aktivní pouze jeden proces. K nastavení aktivního procesu lze použít příkaz `SetCurrentProcess`.

## <a name="example"></a>Příklad

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Viz také
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [Visual Studio aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md)
