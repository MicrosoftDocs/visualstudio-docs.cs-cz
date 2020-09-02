---
title: 'Chyba: RPC vyžaduje ověření | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535733"
---
# <a name="error-rpc-requires-authentication"></a>Chyba: RPC vyžaduje ověření.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio se nemůže připojit ke vzdálenému počítači. Zásada RPC je povolena v místním počítači, což znemožňuje vzdálené ladění.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Spustit `\` *windir*`\system32\regedt32.exe`  
  
2. Vyhledejte a odstraňte `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .  
  
3. Restartujte počítač, aby se změna v registru projevila.  
  
4. Pokud se problém opakuje, obraťte se na správce domény o **konfiguraci počítače->šablony pro správu->>vzdáleného volání procedur – >omezení pro neověřené zásady skupiny klientů RPC** .
