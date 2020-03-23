---
title: Instalace sady Visual Studio s použitím parametrů příkazového řádku
titleSuffix: ''
description: Přečtěte si, jak pomocí parametrů příkazového řádku řídit nebo přizpůsobit instalaci sady Visual Studio.
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7210a2834dda749cfe1d89b9093cd627b7c0ae1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114368"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Instalace sady Visual Studio s použitím parametrů příkazového řádku

Při instalaci sady Visual Studio z příkazového řádku můžete k řízení nebo přizpůsobení instalace použít různé parametry příkazového řádku. Z příkazového řádku můžete provádět následující akce:

- Spusťte instalaci s předvybranými možnostmi.
- Automatizujte proces instalace.
- Vytvořte mezipaměť (rozložení) instalačních souborů pro pozdější použití.

Možnosti příkazového řádku se používají ve spojení s zaváděcím nástrojem nastavení, což je malý soubor (1 MB), který iniciuje proces stahování. Zaváděcí nástroj je první spustitelný soubor, který se spustí při stahování z webu sady Visual Studio.

::: moniker range="vs-2017"

Pokud chcete získat zaváděcí nástroj pro Visual Studio 2017, podívejte se na stránku pro stažení [**předchozích verzí Visual Studia,**](https://visualstudio.microsoft.com/vs/older-downloads/) kde najdete podrobnosti o tom, jak to udělat.

::: moniker-end

::: moniker range="vs-2019"

Pomocí následujících odkazů získáte přímý odkaz na nejnovější zaváděcí nástroj pro produktovou edici, kterou instalujete:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Společenství](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Soubor zaváděcího nástroje by se měl shodovat s jedním z následujících názvů souborů nebo se mu podobat:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, je toto postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem myši na soubor zaváděcího nástroje, zvolte **Vlastnosti**, zvolte kartu **Podrobnosti** a pak zobrazte číslo **verze produktu.** Chcete-li toto číslo porovnat s verzí sady Visual Studio, podívejte se na stránku [čísla sestavení sady Visual Studio a data vydání.](visual-studio-build-numbers-and-release-dates.md)

## <a name="command-line-parameters"></a>Parametry příkazového řádku

 Parametry příkazového řádku sady Visual Studio nerozlišují malá a velká písmena.

> Syntaxe:`vs_enterprise.exe [command] <options>...`

Podle `vs_enterprise.exe` potřeby je vyměňte pro instalující edici produktu. (Případně můžete použít `vs_installer.exe`.)

>[!TIP]
> Další příklady použití příkazového řádku k instalaci sady Visual Studio naleznete na stránce [Příklady parametrů příkazového řádku.](command-line-parameter-examples.md)

::: moniker range="vs-2017"

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| (prázdné) | Nainstaluje produkt. |
| `modify` | Upraví nainstalovaný produkt. |
| `update` | Aktualizuje nainstalovaný produkt. |
| `repair` | Opravuje nainstalovaný produkt. |
| `uninstall` | Odinstaluje nainstalovaný produkt. |
| `export` | **Novinka ve verzi 15.9**: Exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka:** Lze použít pouze s vs_installer.exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| (prázdné) | Nainstaluje produkt. |
| `modify` | Upraví nainstalovaný produkt. |
| `update` | Aktualizuje nainstalovaný produkt. |
| `repair` | Opravuje nainstalovaný produkt. |
| `uninstall` | Odinstaluje nainstalovaný produkt. |
| `export` | Exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka:** Lze použít pouze s vs_installer.exe. |

::: moniker-end

## <a name="install-options"></a>Možnosti instalace

::: moniker range="vs-2017"

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář instance, na které chcete zajít. Pro příkaz install je to **volitelné** a je-li instance nainstalována. U jiných příkazů je to **topovinné** a je-li dříve nainstalovaná instance nainstalována. |
| `--addProductLang <language-locale>` | **Volitelné**: Během operace instalace nebo úpravy určuje jazykové sady ui, které jsou nainstalovány do produktu. Může se na příkazovém řádku zobrazit vícekrát a přidat více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: Během operace instalace nebo úpravy určuje jazykové sady ui, které mají být odebrány z produktu. Může se na příkazovém řádku zobrazit vícekrát a přidat více jazykových sad. Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: Jeden nebo více úloh nebo ID součástí přidat. Požadované součásti artefaktu jsou nainstalovány, ale nejsou doporučené nebo volitelné součásti. Můžete řídit další součásti `--includeRecommended` globálně pomocí `--includeOptional`a/nebo . Chcete-li zahrnout více úloh nebo `--add` součástí, opakujte příkaz (například `--add Workload1 --add Workload2`). Pro jemnější odstupňovanou kontrolu můžete `;includeRecommended` `;includeOptional` připojit nebo k ID `--add Workload1;includeRecommended` `--add Workload2;includeRecommended;includeOptional`(například nebo ). Další informace naleznete na stránce [Pracovní vytížení a ID součástí.](workload-and-component-ids.md) Tuto možnost můžete podle potřeby opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné:** Jeden nebo více úloh nebo ID součástí odebrat. Další informace najdete na stránce [Pracovní vytížení a ID součástí.](workload-and-component-ids.md) Tuto možnost můžete podle potřeby opakovat.|
| `--in <path>` | **Volitelné**: Identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**: Určuje, zda chcete nainstalovat všechny úlohy a součásti pro produkt. |
| `--allWorkloads` | **Volitelné**: Nainstaluje všechny úlohy a součásti, žádné doporučené nebo volitelné součásti. |
| `--includeRecommended` | **Volitelné**: Zahrnuje doporučené součásti pro všechny úlohy, které jsou nainstalovány, ale ne volitelné součásti. Úlohy jsou určeny `--allWorkloads` `--add`buď s nebo . |
| `--includeOptional` | **Volitelné**: Zahrnuje volitelné součásti pro všechny úlohy, které jsou nainstalovány, ale ne doporučené součásti. Úlohy jsou určeny `--allWorkloads` `--add`buď s nebo .  |
| `--quiet, -q` | **Volitelné**: Při instalaci nezobrazovat žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: Zobrazte uživatelské rozhraní, ale nepožadují žádnou interakci od uživatele. |
| `--norestart` | **Volitelné**: Pokud jsou `--passive` k `--quiet` dispozici, příkazy s nebo nebudou automaticky restartovat počítač (v případě potřeby).  To je ignorováno, `--passive` `--quiet` pokud ani nejsou zadány.  |
| `--nickname <name>` | **Volitelné**: Definuje přezdívku, kterou chcete přiřadit instalovanému produktu. Přezdívka nesmí být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: Definuje kód Product Key, který se má použít pro nainstalovaný produkt. Skládá se z 25 alfanumerických znaků `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx`buď ve formátu, nebo . |
| `--help, --?, -h, -?` | Zobrazí offline verzi této stránky. |
| `--config <path>` | **Volitelné** a **Nové v 15.9**: Během operace instalace nebo úpravy to určuje úlohy a součásti, které chcete přidat na základě dříve uloženého konfiguračního souboru instalace. Tato operace je aditivní a neodebere žádné úlohy nebo součásti, pokud nejsou k dispozici v souboru. Položky, které se nevztahují na produkt, také nebudou přidány. Během operace exportu to určuje umístění pro uložení konfiguračního souboru instalace. |

::: moniker-end

::: moniker range="vs-2019"

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář instance, na které chcete zajít. Pro příkaz install je to **volitelné** a je-li instance nainstalována. U jiných příkazů je to **topovinné** a je-li dříve nainstalovaná instance nainstalována. |
| `--addProductLang <language-locale>` | **Volitelné**: Během operace instalace nebo úpravy určuje jazykové sady ui, které jsou nainstalovány do produktu. Může se na příkazovém řádku zobrazit vícekrát a přidat více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: Během operace instalace nebo úpravy určuje jazykové sady ui, které mají být odebrány z produktu. Může se na příkazovém řádku zobrazit vícekrát a přidat více jazykových sad. Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: Jeden nebo více úloh nebo ID součástí přidat. Požadované součásti artefaktu jsou nainstalovány, ale nejsou doporučené nebo volitelné součásti. Můžete řídit další součásti `--includeRecommended` globálně pomocí `--includeOptional`a/nebo . Chcete-li zahrnout více úloh nebo `--add` součástí, opakujte příkaz (například `--add Workload1 --add Workload2`). Pro jemnější odstupňovanou kontrolu můžete `;includeRecommended` `;includeOptional` připojit nebo k ID `--add Workload1;includeRecommended` `--add Workload2;includeRecommended;includeOptional`(například nebo ). Další informace naleznete na stránce [Pracovní vytížení a ID součástí.](workload-and-component-ids.md) Tuto možnost můžete podle potřeby opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné:** Jeden nebo více úloh nebo ID součástí odebrat. Další informace najdete na stránce [Pracovní vytížení a ID součástí.](workload-and-component-ids.md) Tuto možnost můžete podle potřeby opakovat.|
| `--in <path>` | **Volitelné**: Identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**: Určuje, zda chcete nainstalovat všechny úlohy a součásti pro produkt. |
| `--allWorkloads` | **Volitelné**: Nainstaluje všechny úlohy a součásti, žádné doporučené nebo volitelné součásti. |
| `--includeRecommended` | **Volitelné**: Zahrnuje doporučené součásti pro všechny úlohy, které jsou nainstalovány, ale ne volitelné součásti. Úlohy jsou určeny `--allWorkloads` `--add`buď s nebo . |
| `--includeOptional` | **Volitelné**: Zahrnuje volitelné součásti pro všechny úlohy, které jsou nainstalovány, ale ne doporučené součásti. Úlohy jsou určeny `--allWorkloads` `--add`buď s nebo .  |
| `--quiet, -q` | **Volitelné**: Při instalaci nezobrazovat žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: Zobrazte uživatelské rozhraní, ale nepožadují žádnou interakci od uživatele. |
| `--norestart` | **Volitelné**: Pokud jsou `--passive` k `--quiet` dispozici, příkazy s nebo nebudou automaticky restartovat počítač (v případě potřeby).  To je ignorováno, `--passive` `--quiet` pokud ani nejsou zadány.  |
| `--nickname <name>` | **Volitelné**: Definuje přezdívku, kterou chcete přiřadit instalovanému produktu. Přezdívka nesmí být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: Definuje kód Product Key, který se má použít pro nainstalovaný produkt. Skládá se z 25 alfanumerických znaků `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx`buď ve formátu, nebo . |
| `--help, --?, -h, -?` | Zobrazí offline verzi této stránky. |
| `--config <path>` | **Volitelné**: Během operace instalace nebo úpravy to určuje úlohy a součásti, které chcete přidat na základě dříve uloženého konfiguračního souboru instalace. Tato operace je aditivní a neodebere žádné úlohy nebo součásti, pokud nejsou k dispozici v souboru. Položky, které se nevztahují na produkt, také nebudou přidány. Během operace exportu to určuje umístění pro uložení konfiguračního souboru instalace. |

::: moniker-end

> [!IMPORTANT]
> Při zadávání více úloh a součástí je `--add` nutné `--remove` zopakovat přepínač příkazového řádku pro každou položku.

## <a name="layout-options"></a>Možnosti rozložení

::: moniker range="vs-2017"

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář pro vytvoření mezipaměti pro instalaci offline. Další informace naleznete [v tématu Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: `--layout` Používá se k přípravě mezipaměti instalace offline s balíčky prostředků se zadaným jazykem (jazyky). Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: Jeden nebo více úloh nebo ID součástí přidat. Požadované součásti artefaktu jsou nainstalovány, ale nejsou doporučené nebo volitelné součásti. Můžete řídit další součásti `--includeRecommended` globálně pomocí `--includeOptional`a/nebo . Pro jemnější odstupňovanou kontrolu můžete `;includeRecommended` `;includeOptional` připojit nebo k ID `--add Workload1;includeRecommended` `--add Workload2;includeOptional`(například nebo ). Další informace naleznete na stránce [Pracovní vytížení a ID součástí.](workload-and-component-ids.md) <br/>**Poznámka:** `--add` Pokud se používá, jsou staženy pouze zadané úlohy a součásti a jejich závislosti. Pokud `--add` není zadán, všechny úlohy a součásti jsou staženy do rozložení.|
| `--includeRecommended` | **Volitelné**: Zahrnuje doporučené součásti pro všechny úlohy, které jsou nainstalovány, ale ne volitelné součásti. Úlohy jsou určeny `--allWorkloads` `--add`buď s nebo . |
| `--includeOptional` | **Volitelné**: Zahrnuje doporučené *a* volitelné součásti pro všechny úlohy zahrnuté v rozvržení. Úlohy jsou určeny pomocí aplikace `--add`.  |
| `--keepLayoutVersion` | **Novinka v 15.3, volitelné**: Použití změn v rozložení bez aktualizace verze rozložení. |
| `--verify` | **Novinka v 15.3, volitelné**: Ověřte obsah rozložení. Jsou uvedeny všechny poškozené nebo chybějící soubory. |
| `--fix` | **Novinka v 15.3, volitelné**: Ověřte obsah rozložení. Pokud jsou některé soubory poškozené nebo chybí, jsou znovu staženy. K opravě rozložení je nutný přístup k internetu. |
| `--clean <one or more paths to catalogs>` | **Novinka v 15.3, volitelné**: Odebere staré verze součástí z rozložení, které bylo aktualizováno na novější verzi. |

| **Rozšířené možnosti instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu pro instanci, která má být nainstalována. To je vyžadováno pro příkaz install a ignorováno pro ostatní příkazy, pokud `--installPath` je zadáno. |
| `--channelUri <uri>` | **Volitelné**: Identifikátor URI manifestu kanálu. Pokud aktualizace nejsou žádoucí, `--channelUri` můžete přejděte na neexistující soubor (například --channelUri C:\doesntExist.chman). To lze použít pro příkaz install; je ignorována pro ostatní příkazy. |
| `--installChannelUri <uri>` | **Volitelné**: Identifikátor URI manifestu kanálu, který se má použít pro instalaci. Identifikátor URI `--channelUri` určený (který musí `--installChannelUri` být zadán, pokud je zadán) se používá ke zjišťování aktualizací. To lze použít pro příkaz install; je ignorována pro ostatní příkazy. |
| `--installCatalogUri <uri>` | **Volitelné**: Identifikátor URI manifestu katalogu, který se má použít pro instalaci. Pokud je zadán, správce kanálu se pokusí stáhnout manifest katalogu z tohoto identifikátoru URI před použitím identifikátoru URI v manifestu instalačního kanálu. Tento parametr se používá pro podporu offline instalace, kde bude vytvořena mezipaměť rozložení s již staženým katalogem produktů. To lze použít pro příkaz install; je ignorována pro ostatní příkazy. |
| `--productId <id>` | **Nepovinné** ID produktu pro instanci, která bude nainstalována. Toto je předem vyplněno za normálních podmínek instalace. |
| `--wait` | **Volitelné**: Proces bude čekat, dokud nebude instalace dokončena před vrácením ukončovacího kódu. To je užitečné při automatizaci instalací, kde je třeba počkat na dokončení instalace pro zpracování návratového kódu z této instalace. |
| `--locale <language-locale>` | **Volitelné**: Změna jazyka zobrazení uživatelského rozhraní samotného instalačního programu. Nastavení bude zachováno. Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--cache` | **Novinka v 15.2, volitelně**: Pokud jsou k dispozici, budou balíky po instalaci pro následné opravy uchovávány. Tím přepíšete nastavení globálních zásad, které se má použít pro následné instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. Tento příkaz je pro příkaz odinstalace ignorován. Další informace naleznete v části Jak [zakázat nebo přesunout mezipaměť balíčků.](disable-or-move-the-package-cache.md) |
| `--nocache` | **Novinka v 15.2, volitelně**: Pokud jsou k dispozici, budou balíčky po instalaci nebo opravě odstraněny. Budou znovu staženy pouze v případě potřeby a po použití znovu smazány. Tím přepíšete nastavení globálních zásad, které se má použít pro následné instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. Tento příkaz je pro příkaz odinstalace ignorován. Další informace naleznete v části Jak [zakázat nebo přesunout mezipaměť balíčků.](disable-or-move-the-package-cache.md) |
| `--noUpdateInstaller` | **Novinka v 15.2, volitelné**: Pokud je k dispozici, zabrání instalačnímu programu v aktualizaci sám, když je zadán tichý. Instalační program selže příkaz a vrátí nenulový ukončovací kód, pokud je noUpdateInstaller zadán s quiet, když je vyžadována aktualizace instalačního programu. |
| `--noWeb` | **Novinka v 15.3, volitelné**: Pokud je k dispozici, nastavení sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdaří.  Další informace naleznete v [tématu Nasazení ze síťové instalace](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité:** Tento přepínač nezastaví nastavení sady Visual Studio z kontroly aktualizací. Další informace naleznete v [tématu Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Novinka v 15.7, volitelné**: Používá se k určení vlastních instalačních cest pro instalaci. Podporované názvy cest jsou sdíleny, mezipaměti a instalace. |
| `--path cache=<path>` | **Novinka v 15.7, volitelné**: Používá umístění, které zadáte ke stažení instalačních souborů. Toto umístění lze nastavit pouze při prvním instalaci sady Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novinka v 15.7, volitelné**: Obsahuje sdílené soubory pro souběžné instalace sady Visual Studio. Některé nástroje a sady SDK se instalují do umístění na této jednotce, zatímco jiné mohou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: Tuto sadu lze nastavit pouze jednou a při prvním instalaci sady Visual Studio. |
| `--path install=<path>` | **Novinka v 15.7, nepovinné**: Ekvivalentní . `–-installPath` Konkrétně, `--installPath "C:\VS"` `--path install="C:\VS"` a jsou rovnocenné. Současně lze použít pouze jeden z těchto příkazů. |

::: moniker-end

::: moniker range="vs-2019"

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář pro vytvoření mezipaměti pro instalaci offline. Další informace naleznete [v tématu Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: `--layout` Používá se k přípravě mezipaměti instalace offline s balíčky prostředků se zadaným jazykem (jazyky). Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: Jeden nebo více úloh nebo ID součástí přidat. Požadované součásti artefaktu jsou nainstalovány, ale nejsou doporučené nebo volitelné součásti. Můžete řídit další součásti `--includeRecommended` globálně pomocí `--includeOptional`a/nebo . Pro jemnější odstupňovanou kontrolu můžete `;includeRecommended` `;includeOptional` připojit nebo k ID `--add Workload1;includeRecommended` `--add Workload2;includeOptional`(například nebo ). Další informace naleznete na stránce [Pracovní vytížení a ID součástí.](workload-and-component-ids.md) <br/>**Poznámka:** `--add` Pokud se používá, jsou staženy pouze zadané úlohy a součásti a jejich závislosti. Pokud `--add` není zadán, všechny úlohy a součásti jsou staženy do rozložení.|
| `--includeRecommended` | **Volitelné**: Zahrnuje doporučené součásti pro všechny úlohy, které jsou nainstalovány, ale ne volitelné součásti. Úlohy jsou určeny `--allWorkloads` `--add`buď s nebo . |
| `--includeOptional` | **Volitelné**: Zahrnuje doporučené *a* volitelné součásti pro všechny úlohy zahrnuté v rozvržení. Úlohy jsou určeny pomocí aplikace `--add`.  |
| `--keepLayoutVersion` | **Volitelné**: Použití změn v rozložení bez aktualizace verze rozložení. |
| `--verify` | **Volitelné**: Ověřte obsah rozložení. Jsou uvedeny všechny poškozené nebo chybějící soubory. |
| `--fix` | **Volitelné**: Ověřte obsah rozložení.  Pokud jsou některé soubory poškozené nebo chybí, jsou znovu staženy. K opravě rozložení je nutný přístup k internetu. |
| `--clean <one or more paths to catalogs>` | **Volitelné**: Odebere staré verze součástí z rozložení, které bylo aktualizováno na novější verzi. |

| **Rozšířené možnosti instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu pro instanci, která má být nainstalována. To je vyžadováno pro příkaz install a ignorováno pro ostatní příkazy, pokud `--installPath` je zadáno. |
| `--channelUri <uri>` | **Volitelné**: Identifikátor URI manifestu kanálu. Pokud aktualizace nejsou žádoucí, `--channelUri` můžete přejděte na neexistující soubor (například --channelUri C:\doesntExist.chman). To lze použít pro příkaz install; je ignorována pro ostatní příkazy. |
| `--installChannelUri <uri>` | **Volitelné**: Identifikátor URI manifestu kanálu, který se má použít pro instalaci. Identifikátor URI `--channelUri` určený (který musí `--installChannelUri` být zadán, pokud je zadán) se používá ke zjišťování aktualizací. To lze použít pro příkaz install; je ignorována pro ostatní příkazy. |
| `--installCatalogUri <uri>` | **Volitelné**: Identifikátor URI manifestu katalogu, který se má použít pro instalaci. Pokud je zadán, správce kanálu se pokusí stáhnout manifest katalogu z tohoto identifikátoru URI před použitím identifikátoru URI v manifestu instalačního kanálu. Tento parametr se používá pro podporu offline instalace, kde bude vytvořena mezipaměť rozložení s již staženým katalogem produktů. To lze použít pro příkaz install; je ignorována pro ostatní příkazy. |
| `--productId <id>` | **Nepovinné** ID produktu pro instanci, která bude nainstalována. Toto je předem vyplněno za normálních podmínek instalace. |
| `--wait` | **Volitelné**: Proces bude čekat, dokud nebude instalace dokončena před vrácením ukončovacího kódu. To je užitečné při automatizaci instalací, kde je třeba počkat na dokončení instalace pro zpracování návratového kódu z této instalace. |
| `--locale <language-locale>` | **Volitelné**: Změna jazyka zobrazení uživatelského rozhraní samotného instalačního programu. Nastavení bude zachováno. Další informace naleznete v části [Seznam národních prostředí jazyků](#list-of-language-locales) na této stránce.|
| `--cache` | **Volitelné**: Pokud jsou k dispozici, budou balíky po instalaci uchovávány pro následné opravy. Tím přepíšete nastavení globálních zásad, které se má použít pro následné instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. Tento příkaz je pro příkaz odinstalace ignorován. Další informace naleznete v části Jak [zakázat nebo přesunout mezipaměť balíčků.](disable-or-move-the-package-cache.md) |
| `--nocache` | **Volitelné**: Pokud jsou k dispozici, budou balíčky po instalaci nebo opravě odstraněny. Budou znovu staženy pouze v případě potřeby a po použití znovu smazány. Tím přepíšete nastavení globálních zásad, které se má použít pro následné instalace, opravy nebo úpravy. Výchozí zásadou je ukládání balíčků do mezipaměti. Tento příkaz je pro příkaz odinstalace ignorován. Další informace naleznete v části Jak [zakázat nebo přesunout mezipaměť balíčků.](disable-or-move-the-package-cache.md) |
| `--noUpdateInstaller` | **Volitelné**: Pokud je k dispozici, zabrání instalačnímu programu v aktualizaci sám, když je zadán tichý. Instalační program selže příkaz a vrátí nenulový ukončovací kód, pokud je noUpdateInstaller zadán s quiet, když je vyžadována aktualizace instalačního programu. |
| `--noWeb` | **Volitelné**: Pokud je k dispozici, nastavení sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdaří.  Další informace naleznete v [tématu Nasazení ze síťové instalace](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité:** Tento přepínač nezastaví nastavení sady Visual Studio z kontroly aktualizací. Další informace naleznete v [tématu Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md). **Novinka v 16.3.5**: Tento přepínač zabraňuje chybám a zlepšuje výkon s offline instalacemi a aktualizacemi.|
| `--path <name>=<path>` | **Volitelné**: Slouží k určení vlastních instalačních cest pro instalaci. Podporované názvy cest jsou sdíleny, mezipaměti a instalace. |
| `--path cache=<path>` | **Volitelné**: Používá umístění, které zadáte ke stažení instalačních souborů. Toto umístění lze nastavit pouze při prvním instalaci sady Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Volitelné**: Obsahuje sdílené soubory pro souběžné instalace sady Visual Studio. Některé nástroje a sady SDK se instalují do umístění na této jednotce, zatímco jiné mohou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: Tuto sadu lze nastavit pouze jednou a při prvním instalaci sady Visual Studio. |
| `--path install=<path>` | **Nepovinné**: `–-installPath`Odpovídá . Konkrétně, `--installPath "C:\VS"` `--path install="C:\VS"` a jsou rovnocenné. Současně lze použít pouze jeden z těchto příkazů. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Seznam ID pracovního vytížení a ID součástí

Seznam úloh a ID součástí seřazených podle produktu Visual Studio najdete na stránce [ID úloh y visual studia a id komponent.](workload-and-component-ids.md)

## <a name="list-of-language-locales"></a>Seznam jazykových národních prostředí

| **Jazyk-národní prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| Cs-cz | Čeština |
| De-de | Němčina |
| En-us | Angličtina |
| Es-es | Španělština |
| Fr-fr | Francouzština |
| Je to-it | Italština |
| Ja-jp | Japonština |
| Ko-kr | Korejština |
| Pl-pl | Polština |
| Pt-br | Portugalština – Brazílie |
| Ru-ru | Ruština |
| Tr-tr | Turečtina |
| Žh-č | Čínština – zjednodušená |
| Žh-tw | Čínština - tradiční |

## <a name="error-codes"></a>Kódy chyb

V závislosti na výsledku `%ERRORLEVEL%` operace je proměnná prostředí nastavena na jednu z následujících hodnot:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Každá operace generuje několik souborů `%TEMP%` protokolu v adresáři, které označují průběh instalace. Seřaďte složku podle data a `dd_bootstrapper` `dd_client`vyhledejte `dd_setup` soubory, které začínají na , a pro zaváděcí nástroj, instalační aplikaci a instalační modul.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Příklady parametrů příkazového řádku pro instalaci sady Visual Studio](command-line-parameter-examples.md)
- [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizace instalace sady Visual Studio souborem odpovědí](automated-installation-with-response-file.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
