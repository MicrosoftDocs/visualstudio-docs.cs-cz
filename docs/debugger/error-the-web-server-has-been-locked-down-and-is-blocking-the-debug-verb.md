---
title: Webový server byl uzamčen a blokuje příkaz DEBUG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
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
ms.openlocfilehash: e68ab09d7fc398d45a8942c3df4ca0dee5754d2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871206"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Chyba: Webový server byl uzamčen a blokuje příkaz DEBUG.
Krokování webové aplikace nebo webové služby XML se nezdařilo, protože byl spuštěn nástroj IIS Lockdown a byl nainstalován a aktivován nástroj URLScan. Tento stav blokuje službě IIS příjem příkazu ladění.

 URLScan je bezpečnostní nástroj, který spolupracuje s nástrojem Lockdown služby IIS, aby správcům webů služby IIS poskytoval možnost vypnout nepotřebné funkce a omezit typ požadavků HTTP, které bude server zpracovávat. Blokováním konkrétních požadavků HTTP nástroj URLScan Security zabrání tomu, aby potenciálně škodlivé požadavky dosáhly serveru a způsobila poškození.

 Pokud je vaše aplikace spuštěná ve službě IIS 6,0 ve Windows serveru 2003, nemusíte spouštět nástroj IIS Lockdown, protože služba IIS 6,0 nabízí stejné funkce.

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Povolení ladění na webovém serveru s nainstalovaným nástrojem URLScan

1. Vyhledejte soubor Urlscan.ini. Normálně se nachází v adresáři, který vypadá nějak takto:

     C:\WINNT\System32\Inetsrv\urlscan

2. Vytvořte kopii souboru a pojmenujte ho **URLScan. old**.

3. Otevřete původní kopii souboru Urlscan.ini pomocí poznámkového bloku nebo textového editoru dle vašeho výběru.

4. V Urlscan.ini vyhledejte část [AllowVerbs]. Přidejte LADIT do oddílu [AllowVerbs]. Pokud se v části [AllowVerbs] zobrazí;D EBUG, odeberte středník a odkomentujte operaci.

5. Vyhledejte část [DenyVerbs]. Pokud se v části [DenyVerbs] objeví ladění, odeberte ho.

6. Soubor uložte.

7. Restartujte server nebo restartujte službu IIS.

## <a name="see-also"></a>Viz také
- [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Chyba: Webový server nenašel požadovaný prostředek.](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)