---
title: Osvědčené postupy při vývoji pro modelu COM, VSTO a VBA doplňky sady Office
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f821b9769b9353fbee6379ddc1b3826f87ac2de
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671090"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Osvědčené postupy při vývoji pro modelu COM, VSTO a VBA doplňky sady Office
  Pokud vyvíjíte modelu COM, VSTO nebo VBA doplňky pro Office, dodržujte doporučené postupy vývoje popsaných v tomto článku.   To vám pomůže zajistit:

-  Kompatibilita doplňky napříč různými verzemi a nasazení Office.
-  Menší složitost nasazení doplňku pro uživatele a správce IT.
-  Nežádoucí selhání instalace nebo modulu runtime vašeho doplňku nedojde.

>Poznámka: Pomocí [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root) Příprava vašeho modelu COM, VSTO nebo VBA doplněk pro Windows Store se nepodporuje. Doplňky modelu COM, VSTO a VBA nelze distribuovat ve Windows Store nebo Office Store. 
  
## <a name="do-not-check-for-office-during-installation"></a>Nezaškrtávejte políčko pro Office v průběhu instalace  
 Nedoporučujeme s váš doplněk zjištění instalovaného Office během procesu instalace doplňku. Pokud není nainstalovaný Office, můžete nainstalovat doplněk a uživatel bude mít přístup k po dokončení instalace Office. 
  
## <a name="use-embedded-interop-types-nopia"></a>Použití vestavěné typy spolupráce (NoPIA)  
Pokud vaše řešení používá rozhraní .NET 4.0 nebo novější, použijte vložené typy spolupráce (NoPIA) místo v závislosti na Office primární spolupráce sestavení (PIA) redistributable. Pomocí vkládání typ zmenší velikost instalaci vašeho řešení a zajišťuje budoucí kompatibilitu. Office 2010 byl poslední verzi Office, dodávané PIA redistributable. Další informace najdete v tématu [návod: vložení informací o typu ze sestavení Microsoft Office](https://msdn.microsoft.com/library/ee317478.aspx) a [ekvivalence typů a vestavěné typy spolupráce](/windows/uwp/porting/desktop-to-uwp-root).

Pokud vaše řešení používá starší verzi rozhraní .NET, doporučujeme aktualizovat vaše řešení, aby používalo rozhraní .NET 4.0 nebo novější. Pomocí rozhraní .NET 4.0 nebo novější snižuje požadavky na modul runtime na novější verze systému Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Vyhněte se v závislosti na konkrétní verze sady Office  
Pokud vaše řešení používá funkce, které jsou k dispozici v novějších verzích Office, ověřte, zda funkce existuje (Pokud je to možné, na úrovni funkcí) za běhu (například používání výjimek zpracování nebo kontrolou verze). Ověřit minimální verze, místo konkrétních verzí, pomocí rozhraní API podporované v objektovém modelu, jako [Application.Version vlastnost](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Nedoporučujeme, protože ty můžete změnit mezi instalací, prostředí a verzí spoléhat na Office binární metadat instalačními cestami a klíče registru.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Povolit používání 32bitová verze a 64bitová verze Office   
Výchozí cíl sestavení by měly podporovat (x86) 32bitové a 64bitové (x64), pokud vaše řešení závisí na knihovny, které jsou dostupné jenom pro konkrétní bitové verze. Přijetí, zejména v prostředích velký objem dat roste 64bitovou verzi systému Office. Podporuje 32bitové i 64bitové usnadňuje uživatelům přechod mezi 32bitové a 64bitové verze systému Office.

Když píšete kód VBA, použití 64-bit deklarovat příkazy a převod proměnné podle potřeby. Dále ověřte, že dokumenty lze sdílet mezi uživateli, kteří používají 32bitové nebo 64bitové verze Office tím, že poskytuje kód pro každý bitové verze. Další informace najdete v tématu [64bitovým kompilátorem jazyka Visual Basic for applications – přehled](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Podporu prostředí s omezeným přístupem   
Vaše řešení, neměli byste potřebovat oprávnění správce nebo uživatel účtu ke zvýšení úrovně oprávnění. Kromě toho řešení neměl záviset na nastavení nebo změna:

- Aktuální pracovní adresář.
- Adresáře, načtení knihovny DLL.
- Proměnné PATH.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Uložení změnit umístění sdílených dat a nastavení
Pokud řešení obsahuje doplněk a proces, který je externí pro Office, nepoužívejte k výměně dat nebo nastavení mezi doplněk a externí proces složce data aplikací uživatele nebo registru. Místo toho zvažte použití uživatele dočasné složky, složky Dokumenty nebo instalačního adresáře vašeho řešení.

## <a name="increment-the-version-number-with-each-update"></a>Zvýšit číslo verze při každé aktualizaci
Nastavte číslo verze binárních souborů ve vašem řešení a zvýší při každé z nich. To vám usnadní to pro uživatele k identifikování změn mezi verzemi a vyhodnotit kompatibilitu.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Poskytuje příkazy podpory pro nejnovější verze sady Office
Zákazníci žádáme, nezávislým výrobcům softwaru poskytují příkazy podpory pro jejich modelu COM, VSTO a VBA doplňky, které běží v Office. Výpis explicitní podporu příkazy pomáhá zákazníkům pomocí Office 365 ProPlus pochopit připravenosti nástroje podpory. 

Pokud chcete zadat příkazy podpory pro klientské aplikace Office (například Word nebo Excel), nejdříve ověřte, že poběží v aktuální verzi Office doplňky a poté potvrďte k poskytování aktualizací, pokud doplněk přestane fungovat v budoucí verzi. Nemáte k testování doplňky, když společnost Microsoft vydává nové sestavení nebo aktualizace Office. Microsoft mění jen zřídka rozšiřitelnosti platformy modelu COM, VSTO a VBA v Office a tyto změny budou dobře zdokumentovat.

>Důležité: Microsoft udržuje seznam podporovaných doplňky pro sestavy připravenost a kontaktní údaje nezávislý výrobce softwaru. Pokud chcete získat doplněk uvedené, naleznete v tématu [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Ladění instalace nebo načítání problémy pomocí monitorování procesu
Pokud váš doplněk má problémy s kompatibilitou během instalace nebo zatížení, může být související s problémy při přístupu k souborům a registru. Použití [monitorování procesu](/sysinternals/downloads/procmon) nebo něco podobného ladicí protokolování a porovnání chování pro pracovní prostředí vám pomůže identifikovat problém.
