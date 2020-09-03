---
title: 'Chyba: lokalita používá IP adresu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155755"
---
# <a name="error-site-uses-ip-address"></a>Chyba: Server používá adresu IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K této chybě dojde, když se ladicí program pokusí o automatické připojení k webové aplikaci, která používá IP adresu. K tomu dojde, pokud změníte **identifikaci** webu tak, aby **používala konkrétní IP adresu** ve službě IIS.  
  
 Aby se automatické připojení fungovalo, je potřeba vytvořit projekt s konkrétní IP adresou a nikoli jenom názvem počítače. V opačném případě ladicí program změní název počítače na localhost, což způsobí selhání odeslání příkazu ladění službě IIS.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Místo toho použijte manuální připojení (z nabídky ladění vyberte **připojit k procesu**).  
  
     —nebo—  
  
2. Změnit nastavení **Identifikace webu služby IIS** .  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
