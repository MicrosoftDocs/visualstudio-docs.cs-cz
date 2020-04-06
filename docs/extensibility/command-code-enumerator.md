---
title: Čítač výčtu příkazového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739795"
---
# <a name="command-code-enumerator"></a>Čítač výčtu kódu příkazu
Tento čítač výčtu se používá v možnostech pro [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a [SccPopulateList](../extensibility/sccpopulatelist-function.md)k označení příkazu, pro který jsou zadány možnosti.

## <a name="syntax"></a>Syntaxe

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

SCC_COMMAND_CHECKOUT Odpovídá [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN odpovídá [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT odpovídá [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD odpovídá [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE odpovídá [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF Odpovídá [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY odpovídá [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME Odpovídá [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES odpovídá [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS odpovídá [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
