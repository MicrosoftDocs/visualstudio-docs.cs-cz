---
title: 'Chyba: RPC vyžaduje ověření | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e98daf3697c86eec7767135c9ad85d67cd6e958a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460582"
---
# <a name="error-rpc-requires-authentication"></a>Chyba: RPC vyžaduje ověření.
Ladicí program sady Visual Studio se nemůže připojit ke vzdálenému počítači. Zásada RPC je povolena v místním počítači, což znemožňuje vzdálené ladění.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Spustit `\` *windir*`\system32\regedt32.exe`

2. Vyhledejte a odstraňte `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Restartujte počítač, aby se změna v registru projevila.

4. Pokud potíže potrvají, požádejte správce domény o **konfiguraci počítače > Šablony pro správu > > vzdáleného volání procedur > omezení pro neověřené zásady skupiny klientů RPC** .