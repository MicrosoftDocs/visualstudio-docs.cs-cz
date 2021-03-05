---
description: K této chybě dojde, když se ladicí program pokusí o automatické připojení k webové aplikaci, která používá IP adresu.
title: Lokalita používá IP adresu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa18ea975bacbda38a18c27d19d438ab5b4da0b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146739"
---
# <a name="error-site-uses-ip-address"></a>Chyba: Server používá adresu IP
K této chybě dojde, když se ladicí program pokusí o automatické připojení k webové aplikaci, která používá IP adresu. K tomu dojde, pokud změníte **identifikaci** webu tak, aby **používala konkrétní IP adresu** ve službě IIS.

 Aby se automatické připojení fungovalo, je potřeba vytvořit projekt s konkrétní IP adresou a nikoli jenom názvem počítače. V opačném případě ladicí program změní název počítače na localhost, což způsobí selhání odeslání příkazu ladění službě IIS.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Místo toho použijte manuální připojení (z nabídky ladění vyberte **připojit k procesu**).

     —nebo—

2. Změnit nastavení **Identifikace webu služby IIS** .

## <a name="see-also"></a>Viz také
- [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
