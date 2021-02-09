---
title: RPC vyžaduje ověření | Microsoft Docs
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09901453fc602deaa509ceb15e4c571764d407a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871369"
---
# <a name="error-rpc-requires-authentication"></a>Chyba: RPC vyžaduje ověření.
Ladicí program sady Visual Studio se nemůže připojit ke vzdálenému počítači. Zásada RPC je povolena v místním počítači, což znemožňuje vzdálené ladění.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Spustit `\` *windir*`\system32\regedt32.exe`

2. Vyhledejte a odstraňte `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Restartujte počítač, aby se změna v registru projevila.

4. Pokud potíže potrvají, požádejte správce domény o **konfiguraci počítače > Šablony pro správu > > vzdáleného volání procedur > omezení pro neověřené zásady skupiny klientů RPC** .