---
title: Enumerátor kódu | Microsoft Docs
description: Enumerátor kódu příkazu se používá v možnostech pro SccGetCommandOptions a SccPopulateListto k označení příkazu, pro který jsou možnosti zadány.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b97d5083c4f262ae2d86aeef5ee2627fdc854bcb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901380"
---
# <a name="command-code-enumerator"></a>Enumerátor kódu příkazu
Tento enumerátor se používá v možnostech [pro SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a [SccPopulateList](../extensibility/sccpopulatelist-function.md)k označení příkazu, pro který jsou možnosti zadány.

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
SCC_COMMAND_GET Odpovídá [SccGet.](../extensibility/sccget-function.md)

SCC_COMMAND_CHECKOUT Odpovídá [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN Odpovídá [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT Odpovídá [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD Odpovídá [SccAdd.](../extensibility/sccadd-function.md)

SCC_COMMAND_REMOVE Odpovídá [SccRemove.](../extensibility/sccremove-function.md)

SCC_COMMAND_DIFF Odpovídá [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY Odpovídá [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME Odpovídá [názvu SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES Odpovídá vlastnosti [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS Odpovídá [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
