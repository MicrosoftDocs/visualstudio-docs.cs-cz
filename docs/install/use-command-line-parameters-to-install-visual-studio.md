---
title: Instalace sady Visual Studio s použitím parametrů příkazového řádku
titleSuffix: ''
description: Naučte se používat parametry příkazového řádku k řízení a přizpůsobení instalace sady Visual Studio.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d5bea30b8a046be55ba49a1cc1dbf12e3093585f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935653"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Instalace sady Visual Studio s použitím parametrů příkazového řádku

Při instalaci sady Visual Studio z příkazového řádku můžete použít nejrůznější parametry příkazového řádku pro řízení nebo přizpůsobení instalace. Z příkazového řádku můžete provádět následující akce:

- Spusťte instalaci s určitými možnostmi předem.
- Automatizujte proces instalace.
- Vytvořte mezipaměť (rozložení) instalačních souborů pro pozdější použití.

Možnosti příkazového řádku se používají ve spojení s zaváděcím nástrojem pro instalaci, což je malý (1 MB) soubor, který iniciuje proces stahování. Zaváděcí nástroj je první spustitelný soubor, který se spustí při stažení z webu sady Visual Studio.

::: moniker range="vs-2017"

Další informace o tom, jak to udělat, najdete na stránce pro stažení [**předchozích verzí sady Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) , kde můžete získat zaváděcí nástroj pro visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Pomocí následujících odkazů získáte přímý odkaz na nejnovější zaváděcí nástroj pro vydání verze produktu, který instalujete:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Komunita sady Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Soubor zaváděcího nástroje by se měl shodovat s jedním z následujících názvů souborů:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přejděte na stránku [čísla sestavení sady Visual Studio a data verzí](visual-studio-build-numbers-and-release-dates.md) .

## <a name="command-line-parameters"></a>Parametry příkazového řádku

 V parametrech příkazového řádku sady Visual Studio se nerozlišují malá a velká písmena.

> Syntaktick `vs_enterprise.exe [command] <options>...`

`vs_enterprise.exe`Podle potřeby nahraďte produktovou edici, kterou instalujete. (Případně můžete použít `vs_installer.exe` .)

>[!TIP]
> Další příklady použití příkazového řádku k instalaci sady Visual Studio najdete na stránce s [Příklady parametrů příkazového řádku](command-line-parameter-examples.md) .

::: moniker range="vs-2017"

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| trhnout | Nainstaluje produkt. |
| `modify` | Upraví nainstalovaný produkt. |
| `update` | Aktualizuje nainstalovaný produkt. |
| `repair` | Opraví nainstalovaný produkt. |
| `uninstall` | Odinstaluje nainstalovaný produkt. |
| `export` | **Novinka ve verzi 15,9**: exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka**: dá se použít jenom s vs_installer.exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| trhnout | Nainstaluje produkt. |
| `modify` | Upraví nainstalovaný produkt. |
| `update` | Aktualizuje nainstalovaný produkt. |
| `repair` | Opraví nainstalovaný produkt. |
| `uninstall` | Odinstaluje nainstalovaný produkt. |
| `export` | Exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka**: dá se použít jenom s vs_installer.exe. |

::: moniker-end

## <a name="install-options"></a>Možnosti instalace

::: moniker range="vs-2017"

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář, na kterém se má instance jednat. V případě příkazu install je tato akce **volitelná** a probíhá instalace instance. U ostatních příkazů to je **nutné** a tam, kde byla dříve nainstalovaná instance nainstalována. |
| `--addProductLang <language-locale>` | **Volitelné**: během operace instalace nebo změny určuje jazykové sady uživatelského rozhraní, které jsou nainstalovány v produktu. Může se zobrazit víckrát na příkazovém řádku pro přidání více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: během operace instalace nebo změny určují jazykové sady uživatelského rozhraní, které se mají z produktu odebrat. Může se zobrazit víckrát na příkazovém řádku pro přidání více jazykových sad. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jedno nebo více úloh nebo ID součástí, které chcete přidat. Jsou nainstalovány požadované součásti artefaktu, ale ne doporučené nebo volitelné součásti. Další komponenty můžete řídit globálně pomocí `--includeRecommended` a/nebo `--includeOptional` . Chcete-li zahrnout více úloh nebo součástí, opakujte `--add` příkaz (například `--add Workload1 --add Workload2` ). Pro jemnější ovládací prvek můžete připojit `;includeRecommended` nebo `;includeOptional` k ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeRecommended;includeOptional` ). Další informace najdete na stránce s [ID úloh a komponent](workload-and-component-ids.md) . Tuto možnost můžete podle potřeby opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné**: jedno nebo více úloh nebo ID součástí, které chcete odebrat. Další informace najdete na naší stránce [s ID úloh a komponent](workload-and-component-ids.md) . Tuto možnost můžete podle potřeby opakovat.|
| `--in <path>` | **Volitelné**: identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**: bez ohledu na to, jestli se mají nainstalovat všechny úlohy a součásti produktu. |
| `--allWorkloads` | **Volitelné**: nainstaluje všechny úlohy a součásti bez doporučených nebo volitelných součástí. |
| `--includeRecommended` | **Volitelné**: zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti. Úlohy jsou určené buď pomocí, `--allWorkloads` nebo `--add` . |
| `--includeOptional` | **Volitelné**: zahrnuje volitelné součásti pro všechny nainstalované úlohy, ale ne Doporučené součásti. Úlohy jsou určené buď pomocí, `--allWorkloads` nebo `--add` .  |
| `--quiet, -q` | **Volitelné**: při instalaci nezobrazuje žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: zobrazí uživatelské rozhraní, ale nepožaduje žádné interakce od uživatele. |
| `--norestart` | **Volitelné**: Pokud je k dispozici, příkazy s `--passive` nebo `--quiet` nebudou automaticky restartovat počítač (v případě potřeby).  Tato operace se ignoruje `--passive` , pokud není ani není `--quiet` zadána.  |
| `--nickname <name>` | **Volitelné**: Tato definice definuje přezdívku, která se má přidružit k nainstalovanému produktu. Přezdívka nemůže být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: definuje kód Product Key, který se má použít pro nainstalovaný produkt. Skládá se z 25 alfanumerických znaků buď ve formátu `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` nebo `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Zobrazí offline verzi této stránky. |
| `--config <path>` | **Volitelné** a **nové v 15,9**: během operace instalace nebo úprav se tím určují úlohy a komponenty, které se mají přidat, na základě dříve uloženého konfiguračního souboru instalace. Tato operace je doplňková a nebude odebírat žádné úlohy ani komponenty, pokud nejsou v souboru přítomny. Položky, které se nevztahují na produkt, se také nepřidá. Během operace exportu určuje umístění, kam se má uložit konfigurační soubor instalace. |

::: moniker-end

::: moniker range="vs-2019"

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář, na kterém se má instance jednat. V případě příkazu install je tato akce **volitelná** a probíhá instalace instance. U ostatních příkazů to je **nutné** a tam, kde byla dříve nainstalovaná instance nainstalována. |
| `--addProductLang <language-locale>` | **Volitelné**: během operace instalace nebo změny určuje jazykové sady uživatelského rozhraní, které jsou nainstalovány v produktu. Může se zobrazit víckrát na příkazovém řádku pro přidání více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: během operace instalace nebo změny určují jazykové sady uživatelského rozhraní, které se mají z produktu odebrat. Může se zobrazit víckrát na příkazovém řádku pro přidání více jazykových sad. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jedno nebo více úloh nebo ID součástí, které chcete přidat. Jsou nainstalovány požadované součásti artefaktu, ale ne doporučené nebo volitelné součásti. Další komponenty můžete řídit globálně pomocí `--includeRecommended` a/nebo `--includeOptional` . Chcete-li zahrnout více úloh nebo součástí, opakujte `--add` příkaz (například `--add Workload1 --add Workload2` ). Pro jemnější ovládací prvek můžete připojit `;includeRecommended` nebo `;includeOptional` k ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeRecommended;includeOptional` ). Další informace najdete na stránce s [ID úloh a komponent](workload-and-component-ids.md) . Tuto možnost můžete podle potřeby opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné**: jedno nebo více úloh nebo ID součástí, které chcete odebrat. Další informace najdete na naší stránce [s ID úloh a komponent](workload-and-component-ids.md) . Tuto možnost můžete podle potřeby opakovat.|
| `--in <path>` | **Volitelné**: identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**: bez ohledu na to, jestli se mají nainstalovat všechny úlohy a součásti produktu. |
| `--allWorkloads` | **Volitelné**: nainstaluje všechny úlohy a součásti bez doporučených nebo volitelných součástí. |
| `--includeRecommended` | **Volitelné**: zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti. Úlohy jsou určené buď pomocí, `--allWorkloads` nebo `--add` . |
| `--includeOptional` | **Volitelné**: zahrnuje volitelné součásti pro všechny nainstalované úlohy, ale ne Doporučené součásti. Úlohy jsou určené buď pomocí, `--allWorkloads` nebo `--add` .  |
| `--quiet, -q` | **Volitelné**: při instalaci nezobrazuje žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: zobrazí uživatelské rozhraní, ale nepožaduje žádné interakce od uživatele. |
| `--norestart` | **Volitelné**: Pokud je k dispozici, příkazy s `--passive` nebo `--quiet` nebudou automaticky restartovat počítač (v případě potřeby).  Tato operace se ignoruje `--passive` , pokud není ani není `--quiet` zadána.  |
| `--nickname <name>` | **Volitelné**: Tato definice definuje přezdívku, která se má přidružit k nainstalovanému produktu. Přezdívka nemůže být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: definuje kód Product Key, který se má použít pro nainstalovaný produkt. Skládá se z 25 alfanumerických znaků buď ve formátu `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` nebo `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Zobrazí offline verzi této stránky. |
| `--config <path>` | **Volitelné**: během operace instalace nebo změny určuje úlohy a komponenty, které se mají přidat, na základě dříve uloženého konfiguračního souboru instalace. Tato operace je doplňková a nebude odebírat žádné úlohy ani komponenty, pokud nejsou v souboru přítomny. Položky, které se nevztahují na produkt, se také nepřidá. Během operace exportu určuje umístění, kam se má uložit konfigurační soubor instalace. |

::: moniker-end

> [!IMPORTANT]
> Při zadávání více úloh a součástí je třeba `--add` `--remove` pro každou položku zopakovat přepínač příkazového řádku nebo.

## <a name="layout-options"></a>Možnosti rozložení

::: moniker range="vs-2017"

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář, ve kterém má být vytvořena offline instalační mezipaměť. Další informace najdete v tématu [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: používá se `--layout` pro přípravu offline mezipaměti instalace s balíčky prostředků se zadanými jazyky. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jedno nebo více úloh nebo ID součástí, které chcete přidat. Jsou nainstalovány požadované součásti artefaktu, ale ne doporučené nebo volitelné součásti. Další komponenty můžete řídit globálně pomocí `--includeRecommended` a/nebo `--includeOptional` . Pro jemnější ovládací prvek můžete připojit `;includeRecommended` nebo `;includeOptional` k ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeOptional` ). Další informace najdete na stránce s [ID úloh a komponent](workload-and-component-ids.md) . <br/>**Poznámka**: Pokud `--add` se používá, stáhnou se jenom zadané úlohy a komponenty a jejich závislosti. Pokud `--add` není zadaný, všechny úlohy a komponenty se stáhnou do rozložení.|
| `--includeRecommended` | **Volitelné**: zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti. Úlohy jsou určené buď pomocí, `--allWorkloads` nebo `--add` . |
| `--includeOptional` | **Volitelné**: zahrnuje doporučené *a* volitelné komponenty pro všechny úlohy, které jsou součástí rozložení. Úlohy jsou určené pomocí `--add` .  |
| `--keepLayoutVersion` | **Novinka v 15,3, volitelné**: použít změny rozložení bez aktualizace verze rozložení. |
| `--verify` | **Novinka v 15,3, volitelné**: ověřte obsah rozložení. Zobrazí se všechny poškozené nebo chybějící soubory. |
| `--fix` | **Novinka v 15,3, volitelné**: ověřte obsah rozložení. Pokud jsou některé soubory poškozeny nebo chybí, jsou znovu staženy. K opravě rozložení je nutný přístup k Internetu. |
| `--clean <one or more paths to catalogs>` | **Novinka v 15,3, volitelné**: Odebere staré verze komponent z rozložení, které bylo aktualizováno na novější verzi. |

| **Rozšířené možnosti instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu pro instanci, která se má nainstalovat. To se vyžaduje pro příkaz Install a ignorují se pro ostatní příkazy `--installPath` , pokud je zadaný. |
| `--channelUri <uri>` | **Volitelné**: identifikátor URI manifestu kanálu. Pokud aktualizace nepřejete, `--channelUri` může odkazovat na neexistující soubor (například--parametr channeluri C:\doesntExist.chman). Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installChannelUri <uri>` | **Volitelné**: identifikátor URI manifestu kanálu, který se má použít pro instalaci. Identifikátor URI, který je určen `--channelUri` (který musí být zadán, pokud `--installChannelUri` je zadán), se používá ke zjišťování aktualizací. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installCatalogUri <uri>` | **Volitelné**: identifikátor URI manifestu katalogu, který se má použít pro instalaci. Je-li tento parametr zadán, Správce kanálu se před použitím identifikátoru URI v manifestu instalace kanálu pokusí stáhnout manifest katalogu z tohoto identifikátoru URI. Tento parametr slouží k podpoře offline instalace, kde se vytvoří mezipaměť rozložení s již staženým katalogem produktů. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--productId <id>` | **Volitelné** ID produktu pro instanci, která bude nainstalována. Toto je předem vyplněné za normálních podmínek instalace. |
| `--wait` | **Volitelné**: proces počká, až se instalace dokončí, než se vrátí ukončovací kód. To je užitečné při automatizaci instalací, u kterých je potřeba počkat na dokončení instalace pro zpracování návratového kódu z této instalace. |
| `--locale <language-locale>` | **Volitelné**: změňte jazyk zobrazení uživatelského rozhraní pro samotný instalační program. Nastavení bude trvalé. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--cache` | **Novinka v 15,2, volitelné**: Pokud je k dispozici, balíčky se po instalaci uchovávají pro další opravy. Tím se přepíše nastavení globálních zásad, které se bude používat pro další instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. To je ignorováno pro příkaz uninstall. Další informace najdete [v tématu Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) . |
| `--nocache` | **Novinka v 15,2, volitelné**: Pokud je k dispozici, balíčky se po instalaci nebo opravě odstraní. Budou staženy znovu pouze v případě potřeby a znovu odstraněny po použití. Tím se přepíše nastavení globálních zásad, které se bude používat pro další instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. To je ignorováno pro příkaz uninstall. Další informace najdete [v tématu Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) . |
| `--noUpdateInstaller` | **Novinka v 15,2, volitelné**: Pokud je k dispozici, brání instalačnímu programu v aktualizaci, pokud je zadán tichý čas. Instalační program selže příkaz a vrátí nenulový ukončovací kód, pokud je noUpdateInstaller zadán jako tiché, když je vyžadována aktualizace instalačního programu. |
| `--noWeb` | **Novinka v 15,3, volitelné**: Pokud je k dispozici, instalační program sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdařila.  Další informace najdete v tématu [nasazení z instalace ze sítě](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité**: Tento přepínač neukončí instalaci sady Visual Studio ze zjišťování aktualizací. Další informace najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Novinka v 15,7, volitelné**: slouží k zadání vlastních instalačních cest pro instalaci. Podporované názvy cest jsou sdílené, cache a Install. |
| `--path cache=<path>` | **Novinka v 15,7, volitelné**: používá umístění, které zadáte ke stažení instalačních souborů. Toto umístění je možné nastavit pouze při prvním nainstalování sady Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novinka v 15,7, volitelné**: obsahuje sdílené soubory pro souběžné instalace sady Visual Studio. Některé nástroje a sady SDK se instalují do umístění na této jednotce, zatímco jiní uživatelé můžou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: dá se nastavit jenom jednou a při prvním dokončení instalace sady Visual Studio. |
| `--path install=<path>` | **Novinka v 15,7, volitelné**: ekvivalent `–-installPath` . Konkrétně `--installPath "C:\VS"` a `--path install="C:\VS"` jsou ekvivalentní. V jednom okamžiku lze použít pouze jeden z těchto příkazů. |

::: moniker-end

::: moniker range="vs-2019"

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář, ve kterém má být vytvořena offline instalační mezipaměť. Další informace najdete v tématu [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: používá se `--layout` pro přípravu offline mezipaměti instalace s balíčky prostředků se zadanými jazyky. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jedno nebo více úloh nebo ID součástí, které chcete přidat. Jsou nainstalovány požadované součásti artefaktu, ale ne doporučené nebo volitelné součásti. Další komponenty můžete řídit globálně pomocí `--includeRecommended` a/nebo `--includeOptional` . Pro jemnější ovládací prvek můžete připojit `;includeRecommended` nebo `;includeOptional` k ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeOptional` ). Další informace najdete na stránce s [ID úloh a komponent](workload-and-component-ids.md) . <br/>**Poznámka**: Pokud `--add` se používá, stáhnou se jenom zadané úlohy a komponenty a jejich závislosti. Pokud `--add` není zadaný, všechny úlohy a komponenty se stáhnou do rozložení.|
| `--includeRecommended` | **Volitelné**: zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti. Úlohy jsou určené buď pomocí, `--allWorkloads` nebo `--add` . |
| `--includeOptional` | **Volitelné**: zahrnuje doporučené *a* volitelné komponenty pro všechny úlohy, které jsou součástí rozložení. Úlohy jsou určené pomocí `--add` .  |
| `--keepLayoutVersion` | **Volitelné**: použít změny rozložení bez aktualizace verze rozložení. |
| `--verify` | **Volitelné**: ověřte obsah rozložení. Zobrazí se všechny poškozené nebo chybějící soubory. |
| `--fix` | **Volitelné**: ověřte obsah rozložení.  Pokud jsou některé soubory poškozeny nebo chybí, jsou znovu staženy. K opravě rozložení je nutný přístup k Internetu. |
| `--clean <one or more paths to catalogs>` | **Volitelné**: Odebere staré verze komponent z rozložení, které bylo aktualizováno na novější verzi. |

| **Rozšířené možnosti instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu pro instanci, která se má nainstalovat. To se vyžaduje pro příkaz Install a ignorují se pro ostatní příkazy `--installPath` , pokud je zadaný. |
| `--channelUri <uri>` | **Volitelné**: identifikátor URI manifestu kanálu. Pokud aktualizace nepřejete, `--channelUri` může odkazovat na neexistující soubor (například--parametr channeluri C:\doesntExist.chman). Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installChannelUri <uri>` | **Volitelné**: identifikátor URI manifestu kanálu, který se má použít pro instalaci. Identifikátor URI, který je určen `--channelUri` (který musí být zadán, pokud `--installChannelUri` je zadán), se používá ke zjišťování aktualizací. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installCatalogUri <uri>` | **Volitelné**: identifikátor URI manifestu katalogu, který se má použít pro instalaci. Je-li tento parametr zadán, Správce kanálu se před použitím identifikátoru URI v manifestu instalace kanálu pokusí stáhnout manifest katalogu z tohoto identifikátoru URI. Tento parametr slouží k podpoře offline instalace, kde se vytvoří mezipaměť rozložení s již staženým katalogem produktů. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--productId <id>` | **Volitelné** ID produktu pro instanci, která bude nainstalována. Toto je předem vyplněné za normálních podmínek instalace. |
| `--wait` | **Volitelné**: proces počká, až se instalace dokončí, než se vrátí ukončovací kód. To je užitečné při automatizaci instalací, u kterých je potřeba počkat na dokončení instalace pro zpracování návratového kódu z této instalace. |
| `--locale <language-locale>` | **Volitelné**: změňte jazyk zobrazení uživatelského rozhraní pro samotný instalační program. Nastavení bude trvalé. Další informace najdete v části [seznam národních prostředí](#list-of-language-locales) na této stránce.|
| `--cache` | **Volitelné**: Pokud je k dispozici, budou po instalaci pro další opravy zachovány balíčky. Tím se přepíše nastavení globálních zásad, které se bude používat pro další instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. To je ignorováno pro příkaz uninstall. Další informace najdete [v tématu Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) . |
| `--nocache` | **Volitelné**: Pokud je k dispozici, balíčky budou po instalaci nebo opravě odstraněny. Budou staženy znovu pouze v případě potřeby a znovu odstraněny po použití. Tím se přepíše nastavení globálních zásad, které se bude používat pro další instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. To je ignorováno pro příkaz uninstall. Další informace najdete [v tématu Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) . |
| `--noUpdateInstaller` | **Volitelné**: Pokud je k dispozici, brání instalačnímu programu v aktualizaci, pokud je určena tichá aktualizace. Instalační program selže příkaz a vrátí nenulový ukončovací kód, pokud je noUpdateInstaller zadán jako tiché, když je vyžadována aktualizace instalačního programu. |
| `--noWeb` | **Volitelné**: Pokud je k dispozici, instalační program sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdařila.  Další informace najdete v tématu [nasazení z instalace ze sítě](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité**: Tento přepínač neukončí instalaci sady Visual Studio ze zjišťování aktualizací. Další informace najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md). **Novinka v 16.3.5**: Tento přepínač zabraňuje chybám a zvyšuje výkon při offline instalacích a aktualizacích.|
| `--path <name>=<path>` | **Volitelné**: slouží k zadání vlastních instalačních cest pro instalaci. Podporované názvy cest jsou sdílené, cache a Install. |
| `--path cache=<path>` | **Volitelné**: používá umístění, které zadáte ke stažení instalačních souborů. Toto umístění je možné nastavit pouze při prvním nainstalování sady Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Volitelné**: obsahuje sdílené soubory pro souběžné instalace sady Visual Studio. Některé nástroje a sady SDK se instalují do umístění na této jednotce, zatímco jiní uživatelé můžou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: dá se nastavit jenom jednou a při prvním dokončení instalace sady Visual Studio. |
| `--path install=<path>` | **Volitelné**: ekvivalent `–-installPath` . Konkrétně `--installPath "C:\VS"` a `--path install="C:\VS"` jsou ekvivalentní. V jednom okamžiku lze použít pouze jeden z těchto příkazů. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Seznam ID úloh a ID součástí

Seznam úloh a ID komponent seřazených podle produktu Visual Studio najdete na stránce s [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md) .

## <a name="list-of-language-locales"></a>Seznam jazykových národních prostředí

| **Jazyk – národní prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| Cs-cz | Čeština |
| De-de | Němčina |
| EN-US | Angličtina |
| ES-ES | Španělština |
| Fr-FR | Francouzština |
| IT oddělení IT | Italština |
| Ja-JP | Japonština |
| Ko – kr | Korejština |
| Pl-pl | Polština |
| Pt – br | Portugalština – Brazílie |
| Ru-ru | Ruština |
| TR – tr | Turečtina |
| Zh-CN | Čínština – zjednodušená |
| Zh – TW | Čínština – tradiční |

## <a name="error-codes"></a>Kódy chyb

V závislosti na výsledku operace `%ERRORLEVEL%` je proměnná prostředí nastavena na jednu z následujících hodnot:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Každá operace vygeneruje v adresáři několik souborů protokolu `%TEMP%` , které indikují průběh instalace. Seřaďte složku podle data a vyhledejte soubory, které začínají `dd_bootstrapper` na, `dd_client` a `dd_setup` pro zaváděcí nástroj, aplikaci instalátoru a instalační modul, v uvedeném pořadí.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Příklady parametrů příkazového řádku pro instalaci sady Visual Studio](command-line-parameter-examples.md)
- [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizace instalace sady Visual Studio souborem odpovědí](automated-installation-with-response-file.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
