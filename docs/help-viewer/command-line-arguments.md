---
title: Argumenty příkazového řádku pro Help Content Manager
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e25e213f168739f6fe98d60a6ffbf00237a970b6
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378122"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumenty příkazového řádku pro Help Content Manager

Můžete určit, jak nasazovat a spravovat místní obsah nápovědy pomocí argumentů příkazového řádku pro Help Content Manager (*HlpCtntMgr.exe*). Je nutné spustit skripty pro tento nástroj příkazového řádku s oprávněními správce a tyto skripty nelze spouštět jako službu. Pomocí tohoto nástroje můžete provádět následující úlohy:

-   Přidejte nebo aktualizujte místní obsah nápovědy z disku nebo cloudu.

-   Odeberte obsah místní nápovědy.

-   Přesuňte místní úložiště obsahu nápovědy.

-   Přidat, aktualizovat, odstranit nebo přesunout obsah místní nápovědy tiše.

Syntaxe:

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Příklad:

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

## <a name="switches-and-arguments"></a>Přepínače a argumenty

Následující tabulka definuje přepínače a argumenty, které můžete použít pro nástroj příkazového řádku pro Help Content Manager:

|Přepínač|Povinné?|Arguments|
|------------|---------------|---------------|
|/Operation|Ano|-   **Nainstalujte**– přidá knihy z určeného zdroje instalace do místního úložiště obsahu.<br />     Tento přepínač vyžaduje argument/booklist, argument/sourceuri nebo oba. Pokud nezadáte argument/sourceuri, výchozí hodnota URI sady Visual Studio se používá jako zdroj instalace. Pokud nezadáte argument/booklist, budou nainstalovány všechny knihy na/sourceuri.<br />-   **Odinstalujte**--odstraní knihy, které zadáte z místního úložiště obsahu.<br />     Tento přepínač vyžaduje argument/booklist nebo argument/sourceuri.  Pokud zadáte argument/sourceuri, budou odebrány všechny knihy a argument/booklist je ignorován.<br />-   **Přesunout**– přesune místní úložiště na cestu, kterou zadáte. Výchozí cestu místního úložiště je nastaven jako adresář v rámci *% ProgramData %*<br />     Tento přepínač vyžaduje argumenty/locationpath a/catalogname. Pokud zadáte cestu, která není platná nebo neobsahuje jednotce dostatek volného místa k uložení obsahu, bude do protokolu událostí zaznamenány chybové zprávy.<br />-   **Aktualizovat**--aktualizace témat, které se změnily od byly nainstalovány nebo aktualizovány naposledy.<br />     Tento přepínač vyžaduje argument/sourceuri.|
|/ catalogname|Ano|Určuje název katalogu obsahu.|
|/ Locale|Ne|Určuje národní prostředí produktu, který slouží k zobrazení a správě obsahu pro aktuální instanci Help viewer. Například zadejte `EN-US` pro americkou angličtinu.<br /><br /> Pokud nezadáte národní prostředí, se používá národní prostředí operačního systému. Pokud nelze určit toto národní prostředí, `EN-US` se používá.<br /><br /> Pokud zadáte národní prostředí, která není platná, je zaznamenána chybová zpráva v protokolu událostí.|
|/e|Ne|Zvýší oprávnění správce obsahu nápovědy k oprávnění pro správu, pokud má aktuální uživatel přihlašovací údaje pro správu.|
|/ sourceuri|Ne|Určuje adresu URL, ze kterého je obsah nainstalován (API služby) nebo cesta k souboru instalace obsahu (*.msha*). Adresa URL může odkazovat do skupiny produktů (uzel nejvyšší úrovně) nebo na produktové knihy (uzel úrovně listu) v koncovém bodu ve stylu Visual Studio 2010. Nemusíte zahrnovat lomítko (/) na konci adresy URL. Pokud zahrnete koncové lomítko, bude zpracováno odpovídajícím způsobem.<br /><br /> Zaznamenána chybová zpráva se v případě protokolu Pokud zadáte soubor, který není nalezen, není platný nebo není přístupný, nebo pokud není k dispozici připojení k Internetu, nebo je přerušeno během správy obsahu.|
|/ Vendor|Ne|Určuje dodavatele obsahu produktu, který bude odebrán (například `Microsoft`). Výchozí argument pro tento přepínač je Microsoft.|
|argumentů|Ne|Určuje produktový název knih, které se odeberou. Název produktu je identifikován v *helpcontentsetup.msha* nebo *books.html* soubory, které byly dodány s obsahem. Najednou můžete odebrat knihy pouze z jednoho produktu. Chcete-li odebrání knihy z více produktů, je nutné provést více instalací.|
|/ booklist|Ne|Určuje názvy knih, které mají být spravovány, oddělené mezerami. Hodnoty musí odpovídat formálním názvům, jak je uvedeno na instalačním médiu.<br /><br /> Pokud nezadáte tento argument, jsou nainstalované všechny doporučené knihy pro daný produkt v/sourceuri.<br /><br /> Obsahuje-li název knihy jednu nebo více mezer, uzavřete jej mezi dvojité uvozovky (") tak, aby seznam správně oddělován.<br /><br /> Pokud zadáte parametr/sourceuri, který není platný nebo není dostupný, budou zaznamenány chybové zprávy.|
|/ skuid|Ne|Určuje, skladovou jednotku (SKU) produktu ze zdroje instalace, filtrů a knih, které identifikuje přepínač/sourceuri.|
|/Membership|Ne|-   **Minimální**– nainstaluje minimální sadu obsahu nápovědy na základě jednotky SKU, určíte pomocí přepínače/skuid. Mapování mezi SKU a sadou obsahu je přístupný v rozhraní API služby.<br />-   **Doporučené**– nainstaluje sadu Doporučené knihy pro skladovou Položku, kterou můžete určit pomocí argumentu/skuid. Zdroj instalace je rozhraní API služby nebo *. MSHA*.<br />-   **Úplné**– nainstaluje celou sadu knih pro skladovou Položku, kterou můžete určit pomocí argumentu/skuid. Zdroj instalace je rozhraní API služby nebo *. MSHA*.|
|/ locationpath|Ne|Určuje výchozí složku pro místní obsah nápovědy. Tento přepínač musí používat jenom k instalaci nebo přesunutí obsahu. Pokud zadáte tento přepínač, musíte zadat také/silent přepnout.|
|/silent|Ne|Nainstaluje nebo odebere obsah nápovědy bez výzvy pro uživatele nebo bez zobrazení uživatelského rozhraní, včetně ikonu v oznamovací oblasti. Výstup je zaznamenán v souboru *% Temp %* adresáře. **Důležité:**  Pro tichou instalaci obsahu, je nutné použít digitálně podepsané *.cab* soubory není *.mshc* soubory.|
|/launchingApp|Ne|Definuje kontext aplikace a katalogu při spuštění programu Help viewer bez nadřazené aplikace. Argumenty pro tento přepínač jsou *CompanyName*, *ProductName*, a *číslo_verze* (například `/launchingApp Microsoft,VisualStudio,15.0`).<br /><br /> To je vyžadováno pro instalaci obsahu s/silent parametru.|
|/ wait *sekund*|Ne|Pozastaví instalace, odinstalace a obnovení operací. Pokud pro katalog již probíhá operace, proces bude čekat zadaný počet sekund, abyste mohli pokračovat. Použijte hodnotu 0 pro nekonečně dlouhé čekání.|
|/?|Ne|Obsahuje seznam přepínačů a jejich popisy pro nástroj příkazového řádku pro Help Content Manager.|

### <a name="exit-codes"></a>Kódy ukončení

Když spustíte nástroj příkazového řádku pro správce obsahu nápovědy v bezobslužném režimu, vrátí následující kódy ukončení:

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>Viz také:

- [Příručka pro správce Prohlížeč nápovědy](../help-viewer/administrator-guide.md)
- [Přepíše Help Content Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer 2.2](../help-viewer/overview.md)