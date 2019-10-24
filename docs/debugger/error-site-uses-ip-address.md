---
title: 'Chyba: lokalita používá IP adresu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96786efad0349dec7c9e8e9a02cca40af3668341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737503"
---
# <a name="error-site-uses-ip-address"></a>Chyba: Server používá adresu IP
K této chybě dojde, když se ladicí program pokusí o automatické připojení k webové aplikaci, která používá IP adresu. K tomu dojde, pokud změníte **identifikaci** webu tak, aby **používala konkrétní IP adresu** ve službě IIS.

 Aby se automatické připojení fungovalo, je potřeba vytvořit projekt s konkrétní IP adresou a nikoli jenom názvem počítače. V opačném případě ladicí program změní název počítače na localhost, což způsobí selhání odeslání příkazu ladění službě IIS.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Místo toho použijte manuální připojení (z nabídky ladění vyberte **připojit k procesu**).

     —nebo—

2. Změnit nastavení **Identifikace webu služby IIS** .

## <a name="see-also"></a>Viz také:
- [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)