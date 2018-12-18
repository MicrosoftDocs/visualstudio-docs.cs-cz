---
title: 'Chyba: Webový Server byl uzamčen a blokuje příkaz DEBUG. | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60fffd146516bca57497bfdaaabe0f51407063b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770240"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Chyba: Webový server byl uzamčen a blokuje příkaz DEBUG.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Krokování s vnořením do webové aplikace nebo webové služby XML se nezdařila, protože byl spuštěn nástroj lockdown služby IIS a nainstalovaných a aktivovaných URLScan. K tomuto stavu služby IIS blokuje příjem příkaz DEBUG.  
  
 Nástroj URLScan je nástroj zabezpečení, který funguje ve spojení s nástroji Lockdown služby IIS a poskytuje správcům serveru služby IIS možnost vypnutí zbytečné funkcí a omezení typu požadavky HTTP, které server zpracuje. Nástroj URLScan zabezpečení zákonné zodpovědnosti organizací blokováním specifických požadavků, zabraňuje potenciálně škodlivé požadavky na server přišly a způsobit škody.  
  
 Pokud vaše aplikace běží ve službě IIS 6.0 v systému Windows Server 2003, nemusí spustit nástroje Lockdown služby IIS, protože služba IIS 6.0 poskytuje stejné funkce.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Pokud chcete povolit ladění na webovém serveru s URLScan nainstalovaná  
  
1.  Vyhledejte soubor Urlscan.ini. Za normálních okolností se najít v adresáři, který vypadá přibližně takto:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Vytvořte kopii souboru s názvem **Urlscan.old**.  
  
3.  Otevřete původní kopii souboru Urlscan.ini pomocí poznámkového bloku nebo textovém editoru podle vašeho výběru.  
  
4.  V Urlscan.ini vyhledejte v části [AllowVerbs]. Přidejte do oddílu [AllowVerbs] ladění. Pokud se zobrazí; LADIT v části [AllowVerbs], odebrat středník na Odkomentujte příkaz.  
  
5.  Vyhledejte část [DenyVerbs]. Pokud ladění se zobrazí v části [DenyVerbs], odeberte ji.  
  
6.  Uložte soubor.  
  
7.  Restartujte server nebo restartujte službu IIS.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Chyba: Webový server nenašel požadovaný prostředek.](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)



