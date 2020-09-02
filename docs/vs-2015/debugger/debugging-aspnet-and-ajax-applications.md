---
title: Ladění aplikací ASP.NET a AJAX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e0645cd28e6124e31e19b03489661c6828799cf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686747"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Ladění aplikací ASP.NET a AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací je podobné jako ladění formuláře Windows nebo jakékoli jiné aplikace systému Windows, protože oba typy aplikací zahrnují ovládací prvky a události. Existují však také základní rozdíly mezi těmito dvěma typy aplikací:  
  
- Udržování přehledu o stavu je složitější ve webové aplikaci.  
  
- V aplikaci pro Windows je kód, který se má ladit, většinou v jednom umístění; ve webové aplikaci může být kód na klientovi a na serveru. I když [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] je kód na serveru vše, může být také JavaScript nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kód na straně klienta.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příprava na ladění technologie ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Popisuje kroky, které jsou požadovány pro povolení ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikací.  
  
 [Ladění webových aplikací](../debugger/debugging-web-applications.md)  
 Popisuje, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikaci, včetně skriptovacích aplikací s podporou AJAX.  
  
## <a name="related-sections"></a>Související oddíly  
 [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)  
 Vysvětluje, proč je nutné povolit Pouze můj kód pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] výjimky ladění.  
  
 [Přehled ladění a trasování aplikací AJAX](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Popisuje některé postupy a nástroje, které vám pomohou ladit kód AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Rychlejší ladění kódu pomocí IntelliTrace k zaznamenávání a kontrole historie stavu aplikace bez restartování aplikace. Můžete zobrazit informace o událostech a voláních, ke kterým dochází během běžící aplikace a spustit ladění z těchto bodů v čase. Vyžaduje Visual Studio Ultimate.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění webových aplikací a skriptů](../debugger/debugging-web-applications-and-script.md)   
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)
