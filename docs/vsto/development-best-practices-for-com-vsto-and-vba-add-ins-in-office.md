---
title: 'Osvědčené postupy vývoje: COM, VSTO, & doplňky VBA v Office'
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24cc456058f4a87426261ce53fbecb2d919d6a2d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846351"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Osvědčené postupy vývoje pro Doplňky modelu COM, VSTO a VBA v Office
  Pokud vyvíjíte doplňky modelu COM, VSTO nebo VBA pro Office, postupujte podle osvědčených postupů pro vývoj popsaných v tomto článku.   To vám pomůže zajistit:

- Kompatibilita doplňků v různých verzích a nasazeních Office
- Snížení složitosti nasazení doplňků pro uživatele a správce IT.
- Neúmyslná instalace nebo běhové chyby vašeho doplňku neproběhne.

>Poznámka: použití [mostu pro stolní počítače](/windows/uwp/porting/desktop-to-uwp-root) pro přípravu doplňku com, VSTO nebo VBA pro Windows Store se nepodporuje. Doplňky modelu COM, VSTO a VBA nelze distribuovat ve Windows Storu ani v Office Storu.

## <a name="do-not-check-for-office-during-installation"></a>Nekontrolovat Office během instalace
 Nedoporučujeme, aby váš doplněk zjistil, jestli je Office nainstalovaný během procesu instalace doplňku. Pokud Office není nainstalovaný, můžete doplněk nainstalovat a uživatel k němu bude mít přístup po instalaci Office.

## <a name="use-embedded-interop-types-nopia"></a>Použít vložené typy spolupráce (NoPIA)
Pokud vaše řešení používá rozhraní .NET 4,0 nebo novější, místo závislosti na primárním sestavení Interop (PIA) pro Office použijte vložené typy spolupráce (NoPIA). Použití vkládání typů omezuje velikost instalace vašeho řešení a zajišťuje budoucí kompatibilitu. Office 2010 byl poslední verzí Office, která dodala distribuovatelné součásti PIA. Další informace naleznete v tématu [Návod: vložení informací o typu z systém Microsoft Office sestavení](https://msdn.microsoft.com/library/ee317478.aspx) a [ekvivalenci typů a vložených typů spolupráce](/windows/uwp/porting/desktop-to-uwp-root).

Pokud vaše řešení používá starší verzi rozhraní .NET, doporučujeme, abyste řešení aktualizovali tak, aby používalo .NET 4,0 nebo novější. Použití rozhraní .NET 4,0 nebo vyšší snižuje požadavky na modul runtime v novějších verzích systému Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Nepoužívejte v závislosti na konkrétních verzích Office
Pokud vaše řešení používá funkce, které jsou k dispozici pouze v novějších verzích systému Office, ověřte, zda schopnost existuje (Pokud je to možné, na úrovni funkce) za běhu (například pomocí zpracování výjimek nebo kontrolou verze). Ověřte minimální verze, nikoli konkrétní verze, pomocí podporovaných rozhraní API v objektovém modelu, jako je například [vlastnost Application. Version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Nedoporučujeme spoléhat na binární metadata Office, cesty k instalaci ani klíče registru, protože se můžou měnit mezi instalacemi, prostředími a verzemi.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Povolit jak 32, tak pro 64-bitové využití Office
Váš výchozí cíl sestavení by měl podporovat 32 (x86) i 64-bit (x64), pokud vaše řešení nezávisí na knihovnách, které jsou k dispozici pouze pro konkrétní bitová verze. 64 verze systému Office se zvětšuje při přijetí, zejména v prostředích s velkým objemem dat. Podpora 32 bitů a 64 usnadňuje uživatelům přechod mezi 32-bitovou 64 a 16bitovou verzí systému Office.

Při psaní kódu v jazyce VBA použijte 64 příkazů, které jsou v bezpečí, a podle potřeby převeďte proměnné. Kromě toho zajistěte, aby bylo možné sdílet dokumenty mezi uživateli s 32 nebo 64-bitovou verzí systému Office, a to tak, že pro každý bitová verze poskytnete kód. Další informace najdete v tématu [64-bit Visual Basic pro aplikace – přehled](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Podpora omezených prostředí
Vaše řešení by nemělo vyžadovat zvýšení oprávnění nebo oprávnění správce účtu uživatele. Řešení navíc by nemělo záviset na nastavení nebo změně:

- Aktuální pracovní adresář
- Načte adresáře DLL.
- Proměnná cesty

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Změna umístění pro uložení sdílených dat a nastavení
Pokud se řešení skládá z doplňku a procesu, který je externí pro sadu Office, nepoužívejte složku Application data uživatele ani registr k výměně dat nebo nastavení mezi doplňkem a externím procesem. Místo toho zvažte použití dočasné složky dokumentů uživatele, složky Dokumenty nebo instalačního adresáře vašeho řešení.

## <a name="increment-the-version-number-with-each-update"></a>Zvýšit číslo verze u každé aktualizace
Nastavte číslo verze binárních souborů ve vašem řešení a zvyšte je pomocí každé aktualizace. To uživatelům usnadňuje identifikaci změn mezi verzemi a posouzení kompatibility.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Poskytněte příkazy podpory pro nejnovější verze Office.
Zákazníci žádají nezávislé výrobce softwaru, aby poskytovali příkazy podpory pro Doplňky modelu COM, VSTO a VBA, které běží v Office. Seznamte se s vašimi explicitními příkazy podpory, pomocí kterých si zákazníci můžou vyrozumět vaší podpoře prostřednictvím nástrojů připravenosti pro Office 365.

Chcete-li poskytnout příkazy podpory pro klientské aplikace Office (například Word nebo Excel), nejprve ověřte, zda se doplňky spouštějí v aktuální verzi sady Office, a pak potvrďte poskytnutí aktualizací, pokud je doplněk v budoucí verzi. Nemusíte testovat doplňky, když společnost Microsoft uvolňuje nové sestavení nebo aktualizuje sadu Office. Microsoft zřídka mění platformu rozšiřitelnosti COM, VSTO a VBA v Office a tyto změny budou dobře zdokumentovány.

>Důležité: Microsoft udržuje seznam podporovaných doplňků pro sestavy připravenosti a kontaktní informace ISV. Chcete-li získat uvedený doplněk, přečtěte si téma [https://docs.microsoft.com/configmgr/desktop-analytics/ready-for-windows](https://docs.microsoft.com/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Použití monitorování procesů k ladění problémů s instalací nebo načítáním
Pokud má váš doplněk problémy s kompatibilitou při instalaci nebo načítání, může souviset s problémy s přístupem k souborům nebo k registru. Použijte [monitorování procesů](/sysinternals/downloads/procmon) nebo podobný ladicí nástroj k protokolování a porovnání chování s pracovním prostředím, abyste mohli problém identifikovat.
