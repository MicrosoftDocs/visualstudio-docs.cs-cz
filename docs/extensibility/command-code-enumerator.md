---
title: Enumerátor kódu příkazu | Microsoft Docs
description: Enumerátor kódu příkazu se používá v možnostech pro SccGetCommandOptions a SccPopulateListto k označení příkazu, pro který jsou zadané možnosti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e2df7ca11d5e93a3ae43d2a6bd1d7ccf8dfe5aa6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089703"
---
# <a name="command-code-enumerator"></a>Enumerátor kódu příkazu
Tento enumerátor se používá v možnostech pro [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a [SccPopulateList](../extensibility/sccpopulatelist-function.md)k označení příkazu, pro který jsou zadány možnosti.

## <a name="syntax"></a>Syntax

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Členové
SCC_COMMAND_GET odpovídá [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT odpovídá [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN odpovídá [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT odpovídá [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD odpovídá [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE odpovídá [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF odpovídá [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY odpovídá [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME odpovídá [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES odpovídá [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS odpovídá [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
