---
title: Argumenty příkazového řádku pro správce obsahu pro nápovědu
description: Použijte argumenty příkazového řádku pro nástroj Help Content Manager (HlpCtntMgr.exe) a určete, jak nasadit a spravovat místní obsah v nápovědě.
ms.date: 11/01/2017
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24011c50cf6f8d2204abdaa8b6119f7873470bcf
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91879044"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumenty příkazového řádku pro správce obsahu pro nápovědu

Můžete určit, jak nasadit a spravovat místní obsah pro nápovědu pomocí argumentů příkazového řádku pro aplikaci Help Content Manager (*HlpCtntMgr.exe*). Pro tento nástroj příkazového řádku musíte spustit skripty s oprávněními správce a nemůžete spouštět tyto skripty jako službu. Pomocí tohoto nástroje můžete provádět následující úlohy:

- Umožňuje přidat nebo aktualizovat obsah místní aplikace z disku nebo cloudu.

- Odebrat místní obsah obsahu help.

- Přesuňte místní úložiště obsahu help.

- Umožňuje přidat, aktualizovat, odebrat nebo přesunout místní obsah aplikace v tichém režimu.

Syntaxe:

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Například:

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

>[!NOTE]
> Název katalogu je VisualStudio15 jak pro Visual Studio 2017, tak pro Visual Studio 2019. To může být neočekávané, ale je to proto, že se pro obě verze sady Visual Studio používá stejný prohlížeč nápovědy.

## <a name="switches-and-arguments"></a>Přepínače a argumenty

Následující tabulka definuje přepínače a argumenty, které můžete použít pro nástroj příkazového řádku pro aplikaci Help Content Manager:

|Přepínač|Povinné?|Argumenty|
|------------|---------------|---------------|
|/operation|Yes|-   **Instalace**– přidá knihy ze zadaného zdroje instalace do místního úložiště obsahu.<br />     Tento přepínač vyžaduje argument/booklist, argument/sourceURI nebo obojí. Pokud nezadáte argument/sourceURI, použije se jako zdroj instalace výchozí identifikátor URI sady Visual Studio. Pokud nezadáte argument/booklist, jsou nainstalovány všechny knihy na/sourceUri.<br />-   **Odinstalace**– odstraní knihy, které zadáte z místního úložiště obsahu.<br />     Tento přepínač vyžaduje argument/booklist nebo argument/sourceURI.  Pokud zadáte argument/sourceURI, všechny knihy se odeberou a argument/booklist se ignoruje.<br />-   **Move**– přesune místní úložiště na zadanou cestu. Výchozí cesta místního úložiště se nastaví jako adresář v umístění *% Složka ProgramData%* .<br />     Tento přepínač vyžaduje argumenty/locationPath a/catalogName. Do protokolu událostí se zaprotokolují chybové zprávy, pokud zadáte cestu, která není platná, nebo pokud jednotka neobsahuje dostatek volného místa pro uložení obsahu.<br />-   **Aktualizace**--aktualizuje témata, která se změnila od doby, kdy byla nainstalována nebo naposledy aktualizována.<br />     Tento přepínač vyžaduje argument/sourceURI.|
|/catalogName|Yes|Určuje název katalogu obsahu. Pro Visual Studio 2017 a Visual Studio 2019 se jedná o VisualStudio15.|
|povinný/locale.|No|Určuje národní prostředí produktu, které se používá k zobrazení a správě obsahu pro aktuální instanci aplikace Help Viewer. Například zadáte `EN-US` pro English-United stavy.<br /><br /> Pokud nezadáte národní prostředí, použije se národní prostředí operačního systému. Pokud se toto národní prostředí nedá určit, `EN-US` použije se.<br /><br /> Pokud zadáte neplatnou hodnotu národního prostředí, do protokolu událostí se zaznamená chybová zpráva.|
|/e|No|Pokud má aktuální uživatel pověření správce, zvýší úroveň oprávnění správce obsahu.|
|/sourceURI|No|Určuje adresu URL, ze které se instaluje obsah (rozhraní API služby), nebo cestu k instalačnímu souboru obsahu (*. msha*). Adresa URL může ukazovat na skupinu produktů (uzel nejvyšší úrovně) nebo na produktové knihy (uzel na úrovni listu) ve stylu sady Visual Studio 2010. Na konci adresy URL nemusíte vkládat lomítko (/). Pokud zadáte koncové lomítko, bude zpracováno odpovídajícím způsobem.<br /><br /> V protokolu událostí se zaznamená chybová zpráva, pokud zadáte soubor, který se nenašel, není platný nebo není dostupný, nebo pokud připojení k Internetu není k dispozici nebo se přerušilo při správě obsahu.|
|/vendor|No|Určuje dodavatele obsahu produktu, který se odebere (například `Microsoft` ). Výchozím argumentem pro tento přepínač je Microsoft.|
|/productName|No|Určuje název produktu pro knihy, které se odeberou. Název produktu je identifikovaný v souborech *HelpContentSetup. msha* nebo *books.html* , které byly dodávány s obsahem. Knihy můžete kdykoli odebrat jenom z jednoho produktu. Chcete-li odebrat knihy z více produktů, je nutné provést více instalací.|
|/booklist|No|Určuje názvy knih, které mají být spravovány, oddělené mezerami. Hodnoty se musí shodovat s názvy knih, jak je uvedeno na instalačním médiu.<br /><br /> Pokud tento argument nezadáte, nainstalují se všechny doporučené knihy pro zadaný produkt v/sourceURI.<br /><br /> Pokud název knihy obsahuje jednu nebo více mezer, uzavřete ji do dvojitých uvozovek ("), aby byl seznam odpovídajícím způsobem oddělen.<br /><br /> Pokud zadáte/sourceURI, který není platný nebo není dostupný, budou se zaprotokolovat chybové zprávy.|
|/skuId.|No|Určuje skladovou jednotku uchování (SKU) produktu ze zdroje instalace a filtruje knihy, které/SourceURI přepínač identifikuje.|
|/membership|No|-   **Minimum**– nainstaluje minimální sadu obsahu pomoci založenou na SKU, kterou určíte pomocí přepínače/skuId.. Mapování mezi SKU a sadou obsahu je zveřejněné v rozhraní API služby.<br />-   **Doporučené**– nainstaluje sadu doporučených knih pro skladovou položku, kterou určíte pomocí argumentu/skuId.. Zdroj instalace je rozhraní API služby nebo *. MSHA*.<br />-   **Úplný**– nainstaluje celou sadu knih pro skladovou položku, kterou určíte pomocí argumentu/skuId.. Zdroj instalace je rozhraní API služby nebo *. MSHA*.|
|/locationpath|No|Určuje výchozí složku pro obsah místní složky help. Tento přepínač je nutné použít pouze k instalaci nebo přesunutí obsahu. Pokud zadáte tento přepínač, je nutné zadat také přepínač/Silent.|
|/silent|No|Nainstaluje nebo odebere obsah nápovědy bez zobrazení výzvy uživateli nebo zobrazení libovolného uživatelského rozhraní, včetně ikony v oznamovací oblasti stavu. Výstup se protokoluje do souboru v adresáři *% TEMP%* . **Důležité informace:**  Chcete-li nainstalovat obsah v tichém režimu, je nutné použít digitálně podepsané soubory *. cab* , nikoli soubory *. mshc* .|
|/launchingApp|No|Definuje kontext aplikace a katalogu při spuštění aplikace Help Viewer bez nadřazené aplikace. Argumenty pro tento přepínač jsou *CompanyName*, *NázevVýrobku*a *číslo_verze* (například `/launchingApp Microsoft,VisualStudio,16.0` ).<br /><br /> To je vyžadováno pro instalaci obsahu pomocí parametru/Silent.|
|/Wait *sekund*|No|Pozastaví instalaci, odinstalaci a obnovení operací. Pokud již operace pro katalog probíhá, proces bude čekat na daný počet sekund, než bude pokračovat. Pokud chcete počkat neomezenou dobu, použijte 0.|
|/?|No|Vypíše přepínače a jejich popisy pro nástroj příkazového řádku pro nástroj Help Content Manager.|

### <a name="exit-codes"></a>Ukončovací kódy

Když spustíte nástroj příkazového řádku pro správce obsahu Help v tichém režimu, vrátí následující ukončovací kódy:

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

## <a name="see-also"></a>Viz také

- [Příručka pro správce prohlížeče nápovědy](../help-viewer/administrator-guide.md)
- [Přepsání v nápovědě pro Content Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)