---
title: Ladění aplikací ASP.NET a AJAX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3a600059f29d7e0034e4e64239798c32d721a1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785921"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Ladění aplikací ASP.NET a AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací je podobné ladění formuláře Windows nebo jakékoli jiné aplikace Windows, protože oba typy aplikací zahrnují ovládací prvky a události. Existují však také základní rozdíly mezi těmito dvěma typy aplikací:  
  
-   Udržování přehledu o stavu je složitější ve webové aplikaci.  
  
-   V aplikaci Windows kódu k ladění je většinou na jednom místě; ve webové aplikaci může být kód na straně klienta a na serveru. Zatímco [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kód je všechny na serveru, může také být taktéž jazyk JavaScript nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kód na straně klienta.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příprava na ladění technologie ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Popisuje kroky, které jsou požadovány pro povolení ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikací.  
  
 [Ladění webových aplikací](../debugger/debugging-web-applications.md)  
 Popisuje, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace, jako jsou třeba aplikace s povoleným AJAX skriptu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)  
 Vysvětluje, proč musí být povolena funkce pouze můj kód pro ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] výjimky.  
  
 [Ladění a trasování – přehled jazyka Ajax aplikací](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Tento článek popisuje některé postupy a nástroje, které vám může pomoci ladit váš kód AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Ladění kódu rychleji s použitím technologie IntelliTrace zaznamenávat a kontrolovat historie stavu vaší aplikace bez restartování aplikace tak často. Zobrazí se informace o událostech a volání, k nimž došlo při spouštění vaší aplikace, která začínají ladění těchto bodech v čase. Vyžaduje Visual Studio Ultimate.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění webových aplikací a skriptu](../debugger/debugging-web-applications-and-script.md)   
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)



