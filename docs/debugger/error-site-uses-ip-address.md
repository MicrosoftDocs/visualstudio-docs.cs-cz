---
title: 'Chyba: Lokality používá IP adresu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b726902c57cc95b694f2ab7e656a444ed42a0ba9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470901"
---
# <a name="error-site-uses-ip-address"></a>Chyba: Server používá adresu IP
K této chybě dojde, když se ladicí program se pokusí automaticky připojit k webové aplikaci, která používá IP adresu. K tomu dojde, pokud změníte **identifikaci webu** k **použít konkrétní IP adresu** ve službě IIS.  
  
 Pro automatické připojte k práci, budete muset vytvořit projekt s konkrétní IP adresu, nikoli jen název počítače. Ladicí program, jinak se změní název počítače localhost, což způsobí selhání odeslat příkaz debug do služby IIS.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Místo toho připojit pomocí ruční (v nabídce ladění zvolte **připojit k procesu**).  
  
     —nebo—  
  
2.  Změna **identifikace serveru webové služby IIS** nastavení.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)