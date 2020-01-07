---
title: Instalace sady Visual Studio s použitím parametrů příkazového řádku
titleSuffix: ''
description: Další informace o použití parametrů příkazového řádku k řízení nebo přizpůsobit instalaci sady Visual Studio.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6d985266679d70f24ca2b40077549b5c3354b7f4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590940"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Instalace sady Visual Studio s použitím parametrů příkazového řádku

Při instalaci sady Visual Studio z příkazového řádku můžete použít nejrůznější parametry příkazového řádku pro řízení nebo přizpůsobení instalace. Z příkazového řádku můžete provést následující akce:

- Spusťte instalaci s možnostmi předem vybrali.
- Automatizujte proces instalace.
- Vytvoření mezipaměti (rozložení) instalačních souborů pro pozdější použití.

Možnosti příkazového řádku se používají ve spojení s zaváděcím nástrojem pro instalaci, což je malý (1 MB) soubor, který iniciuje proces stahování. Zaváděcí nástroj je první spustitelný soubor, který se spustí, když si stáhnete z webu Visual Studio.

::: moniker range="vs-2017"

Další informace o tom, jak to udělat, najdete na stránce pro stažení [**předchozích verzí sady Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) , kde můžete získat zaváděcí nástroj pro visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Chcete-li získat přímý odkaz na nejnovější verzi bootstrapper pro edici produktu, které chcete instalovat pomocí následujících odkazů:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Soubor zaváděcího nástroje by se měl shodovat s jedním z následujících názvů souborů:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Pokud jste dříve stáhli soubor zaváděcího nástroje a chcete ověřit jeho verzi, tady je postup. V systému Windows otevřete Průzkumníka souborů, klikněte pravým tlačítkem na soubor zaváděcího nástroje, zvolte **vlastnosti**, klikněte na kartu **Podrobnosti** a pak zobrazte číslo **verze produktu** . Chcete-li toto číslo porovnat s vydáním sady Visual Studio, přejděte na stránku [čísla sestavení sady Visual Studio a data verzí](visual-studio-build-numbers-and-release-dates.md) .

## <a name="command-line-parameters"></a>Parametry příkazového řádku

 Parametry příkazového řádku aplikace Visual Studio jsou malá a velká písmena.

> Syntaxe: `vs_enterprise.exe [command] <options>...`

Podle potřeby nahraďte `vs_enterprise.exe` edicí produktu, kterou instalujete. (Můžete také použít `vs_installer.exe`.)

>[!TIP]
> Další příklady použití příkazového řádku k instalaci sady Visual Studio najdete na stránce s [Příklady parametrů příkazového řádku](command-line-parameter-examples.md) .

::: moniker range="vs-2017"

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| (prázdné) | Nainstaluje produkt. |
| `modify` | Upraví zobrazí nainstalovaný produkt. |
| `update` | Aktualizuje zobrazí nainstalovaný produkt. |
| `repair` | Opraví zobrazí nainstalovaný produkt. |
| `uninstall` | Odinstaluje zobrazí nainstalovaný produkt. |
| `export` | **Novinka ve verzi 15,9**: exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka**: dá se použít jenom s vs_installer. exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| (prázdné) | Nainstaluje produkt. |
| `modify` | Upraví zobrazí nainstalovaný produkt. |
| `update` | Aktualizuje zobrazí nainstalovaný produkt. |
| `repair` | Opraví zobrazí nainstalovaný produkt. |
| `uninstall` | Odinstaluje zobrazí nainstalovaný produkt. |
| `export` | Exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka**: dá se použít jenom s vs_installer. exe. |

::: moniker-end

## <a name="install-options"></a>Možnosti instalace

::: moniker range="vs-2017"

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář pro instance, kterou chcete použít. Pro instalačního příkazu, to je **volitelné** a nainstalovanou instanci. Pro další příkazy jde **vyžaduje** a kam se nainstaloval dříve nainstalovanou instanci. |
| `--addProductLang <language-locale>` | **Volitelné**: během instalace nebo upravte činnost, určuje uživatelského rozhraní jazykových sad, které jsou nainstalovány do produktu. Může se objevit více než jednou v příkazovém řádku, chcete-li přidat více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: během instalace nebo upravte činnost, určuje uživatelského rozhraní jazykových sad, které budou odebrány z produktu. Může se objevit více než jednou v příkazovém řádku, chcete-li přidat více jazykových sad. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jeden nebo více úloh nebo ID komponenty pro přidání. Ale ne doporučené a volitelné komponenty jsou nainstalovány požadované součásti artefaktu. Můžete určit další součásti globálně pomocí `--includeRecommended` a/nebo `--includeOptional`. Chcete-li zahrnout více úloh nebo komponenty, opakujte `--add` příkazu (například `--add Workload1 --add Workload2`). Pro citlivější ovládací prvek, můžete připojit `;includeRecommended` nebo `;includeOptional` ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeRecommended;includeOptional`). Další informace najdete v tématu [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. Tato možnost podle potřeby, můžete opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné**: jeden nebo více úloh nebo ID komponenty odebrat. Další informace najdete v tématu naše [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. Tato možnost podle potřeby, můžete opakovat.|
| `--in <path>` | **Volitelné**: identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**:, jestli se má nainstalovat všechny úlohy a komponenty pro produkt. |
| `--allWorkloads` | **Volitelné**: nainstaluje všechny úlohy a komponenty, žádné doporučené nebo volitelné součásti. |
| `--includeRecommended` | **Volitelné**: obsahuje doporučené komponenty pro všechny úlohy, které jsou nainstalovány, ale nikoli volitelné komponenty. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`. |
| `--includeOptional` | **Volitelné**: zahrnuje volitelné komponenty pro všechny úlohy, které jsou nainstalovány, ale ne doporučené komponenty. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`.  |
| `--quiet, -q` | **Volitelné**: při instalaci nezobrazuje žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: zobrazí uživatelské rozhraní, ale nepožaduje žádné interakce od uživatele. |
| `--norestart` | **Volitelné**: Pokud je k dispozici, příkazy s `--passive` nebo `--quiet` nebudou automaticky restartovat počítač (v případě potřeby).  To je ignorováno, pokud žádná `--passive` ani `--quiet` jsou uvedeny.  |
| `--nickname <name>` | **Volitelné**: definuje Přezdívka přiřadit zobrazí nainstalovaný produkt. Přezdívka nemůže být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: definuje kód product key pro zobrazí nainstalovaný produkt. Skládá se z 25 alfanumerických znaků buď ve formátu `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` nebo `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Zobrazte offline verzi této stránky. |
| `--config <path>` | **Volitelné** a **nový v 15.9**: během instalace nebo upravte činnost, určuje, úlohy a komponenty pro přidání založeny na konfigurační soubor instalace předtím uložili. Tato operace je doplňková a nebude odebírat žádné úlohy ani komponenty, pokud nejsou v souboru přítomny. Položky, které se nevztahují na produkt, se také nepřidá. Během operace exportu určuje umístění pro uložení konfigurační soubor instalace. |

::: moniker-end

::: moniker range="vs-2019"

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář pro instance, kterou chcete použít. Pro instalačního příkazu, to je **volitelné** a nainstalovanou instanci. Pro další příkazy jde **vyžaduje** a kam se nainstaloval dříve nainstalovanou instanci. |
| `--addProductLang <language-locale>` | **Volitelné**: během instalace nebo upravte činnost, určuje uživatelského rozhraní jazykových sad, které jsou nainstalovány do produktu. Může se objevit více než jednou v příkazovém řádku, chcete-li přidat více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: během instalace nebo upravte činnost, určuje uživatelského rozhraní jazykových sad, které budou odebrány z produktu. Může se objevit více než jednou v příkazovém řádku, chcete-li přidat více jazykových sad. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jeden nebo více úloh nebo ID komponenty pro přidání. Ale ne doporučené a volitelné komponenty jsou nainstalovány požadované součásti artefaktu. Můžete určit další součásti globálně pomocí `--includeRecommended` a/nebo `--includeOptional`. Chcete-li zahrnout více úloh nebo komponenty, opakujte `--add` příkazu (například `--add Workload1 --add Workload2`). Pro citlivější ovládací prvek, můžete připojit `;includeRecommended` nebo `;includeOptional` ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeRecommended;includeOptional`). Další informace najdete v tématu [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. Tato možnost podle potřeby, můžete opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné**: jeden nebo více úloh nebo ID komponenty odebrat. Další informace najdete v tématu naše [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. Tato možnost podle potřeby, můžete opakovat.|
| `--in <path>` | **Volitelné**: identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**:, jestli se má nainstalovat všechny úlohy a komponenty pro produkt. |
| `--allWorkloads` | **Volitelné**: nainstaluje všechny úlohy a komponenty, žádné doporučené nebo volitelné součásti. |
| `--includeRecommended` | **Volitelné**: obsahuje doporučené komponenty pro všechny úlohy, které jsou nainstalovány, ale nikoli volitelné komponenty. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`. |
| `--includeOptional` | **Volitelné**: zahrnuje volitelné komponenty pro všechny úlohy, které jsou nainstalovány, ale ne doporučené komponenty. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`.  |
| `--quiet, -q` | **Volitelné**: při instalaci nezobrazuje žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: zobrazí uživatelské rozhraní, ale nepožaduje žádné interakce od uživatele. |
| `--norestart` | **Volitelné**: Pokud je k dispozici, příkazy s `--passive` nebo `--quiet` nebudou automaticky restartovat počítač (v případě potřeby).  To je ignorováno, pokud žádná `--passive` ani `--quiet` jsou uvedeny.  |
| `--nickname <name>` | **Volitelné**: definuje Přezdívka přiřadit zobrazí nainstalovaný produkt. Přezdívka nemůže být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: definuje kód product key pro zobrazí nainstalovaný produkt. Skládá se z 25 alfanumerických znaků buď ve formátu `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` nebo `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Zobrazte offline verzi této stránky. |
| `--config <path>` | **Volitelné**: během operace instalace nebo změny určuje úlohy a komponenty, které se mají přidat, na základě dříve uloženého konfiguračního souboru instalace. Tato operace je doplňková a nebude odebírat žádné úlohy ani komponenty, pokud nejsou v souboru přítomny. Položky, které se nevztahují na produkt, se také nepřidá. Během operace exportu určuje umístění pro uložení konfigurační soubor instalace. |

::: moniker-end

> [!IMPORTANT]
> Při zadávání více úloh a součástí je nutné pro každou položku zopakovat `--add` nebo `--remove` přepínač příkazového řádku.

## <a name="layout-options"></a>Možnosti rozložení

::: moniker range="vs-2017"

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář, který chcete vytvořit offline instalaci mezipaměti. Další informace najdete v tématu [vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: použít s `--layout` Příprava offline instalace mezipaměti pomocí balíčků prostředků se zadaným jazyk(y). Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jeden nebo více úloh nebo ID komponenty pro přidání. Ale ne doporučené a volitelné komponenty jsou nainstalovány požadované součásti artefaktu. Můžete určit další součásti globálně pomocí `--includeRecommended` a/nebo `--includeOptional`. Pro citlivější ovládací prvek, můžete připojit `;includeRecommended` nebo `;includeOptional` ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeOptional`). Další informace najdete v tématu [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. <br/>**Poznámka:** : Pokud `--add` se používá, pouze zadané úlohy a komponenty a jejich závislosti se stáhnou. Pokud `--add` nezadáte, všechny úlohy a komponenty se stáhnou do rozložení.|
| `--includeRecommended` | **Volitelné**: obsahuje doporučené komponenty pro všechny úlohy, které jsou nainstalovány, ale nikoli volitelné komponenty. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`. |
| `--includeOptional` | **Volitelné**: obsahuje doporučené *a* volitelné komponenty pro všechny úlohy nebudou zahrnuty do rozložení. Úlohy jsou zadány s `--add`.  |
| `--keepLayoutVersion` | **Novinka v 15.3, volitelné**: použít změny na rozložení bez aktualizace verze rozložení. |
| `--verify` | **Novinka v 15.3, volitelné**: Ověřte obsah rozložení. Jsou uvedeny všechny soubory poškozen nebo chybí. |
| `--fix` | **Novinka v 15.3, volitelné**: Ověřte obsah rozložení. Pokud jsou některé soubory poškozeny nebo chybí, jsou znovu staženy. Přístup k Internetu je potřeba opravit rozložení. |
| `--clean <one or more paths to catalogs>` | **Novinka v 15.3, volitelné**: Odebere staré verze komponent z rozložení, který byl aktualizován na novější verzi. |

| **Možnosti rozšířené instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu pro instanci k instalaci. To je vyžadováno pro příkaz Install a ignoruje se pro ostatní příkazy, pokud je zadána `--installPath`. |
| `--channelUri <uri>` | **Volitelné**: identifikátor URI manifest kanálu. Pokud aktualizace nepřejete, `--channelUri` může ukazovat na neexistující soubor (například--parametr channeluri C:\doesntExist.chman). Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installChannelUri <uri>` | **Volitelné**: identifikátor URI manifestu kanálu pro instalaci. Určený identifikátor URI `--channelUri` (který musí být zadán při `--installChannelUri` určena) slouží ke zjištění aktualizací. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installCatalogUri <uri>` | **Volitelné**: identifikátor URI manifestu katalogu pro instalaci. Je-li zadána, Správce kanálu se pokusí stáhnout manifest katalogu z tohoto identifikátoru URI před použitím tohoto identifikátoru URI v manifestu kanálu instalace. Tento parametr se používá pro podporu offline instalace, ve kterém se vytvoří mezipaměť rozložení s katalog produktů, které jsou staženy. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--productId <id>` | **Volitelné** ID produktu pro instanci, která se nainstaluje. Toto je předem vyplněné za normálních podmínek instalace. |
| `--wait` | **Volitelné**: proces budou čekat na dokončení instalace před vrácením ukončovací kód. To je užitečné, když automatizace instalace, ve kterém musí jeden čekání na instalaci pro dokončení zpracování návratový kód od instalace. |
| `--locale <language-locale>` | **Volitelné**: změňte jazyk zobrazení uživatelského rozhraní pro samotný instalační služby. Nastavení budou zachována. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--cache` | **Novinka v 15.2, volitelné**: Pokud jsou k dispozici, balíčků se budou uchovávat po nainstalování pro další opravy. Tím se přepíše nastavení pro následné nainstaluje, opraví nebo úpravy globální zásady. Výchozí zásada je do mezipaměti balíčků. To se ignoruje pro příkaz odinstalovat. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `--nocache` | **Novinka v 15.2, volitelné**: Pokud jsou k dispozici, balíčky se odstraní po se nainstalovat ani opravit. Budou staženy znovu pouze v případě potřeby a znovu odstraněny po použití. Tím se přepíše nastavení pro následné nainstaluje, opraví nebo úpravy globální zásady. Výchozí zásada je do mezipaměti balíčků. To se ignoruje pro příkaz odinstalovat. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `--noUpdateInstaller` | **Novinka v 15.2, volitelné**: Pokud jsou k dispozici, lze zabránit instalačnímu programu ze samotné aktualizace, pokud je zadán tichý. Instalační program příkaz selže a vrátí nenulový ukončovací kód, pokud noUpdateInstaller je zadána s quiet, když se vyžaduje se aktualizace instalačního programu. |
| `--noWeb` | **Novinka v 15,3, volitelné**: Pokud je k dispozici, instalační program sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdařila.  Další informace najdete v tématu [nasazení z instalace v síti](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité**: Tento přepínač neukončí instalaci sady Visual Studio ze zjišťování aktualizací. Další informace najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Nové ve verzi 15.7 volitelné**: používá se k určení vlastní instalační cesty pro instalaci. Podporované cesty, které jsou sdíleny názvy, mezipaměť a instalace. |
| `--path cache=<path>` | **Nové ve verzi 15.7 volitelné**: používá umístění, které zadáte ke stažení instalačních souborů. Toto umístění lze nastavit pouze při prvním je nainstalována aplikace Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nové ve verzi 15.7 volitelné**: obsahuje sdílené soubory pro instalaci sady Visual Studio vedle sebe. Některé nástroje a sady SDK nainstalovat do umístění na této jednotce, zatímco jiné můžou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: To lze nastavit pouze jednou a na prvním je nainstalována aplikace Visual Studio. |
| `--path install=<path>` | **Nové ve verzi 15.7 volitelné**: ekvivalentní `–-installPath`. Konkrétně `--installPath "C:\VS"` a `--path install="C:\VS"` jsou ekvivalentní. V jednom okamžiku lze použít pouze jeden z těchto příkazů. |

::: moniker-end

::: moniker range="vs-2019"

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář, který chcete vytvořit offline instalaci mezipaměti. Další informace najdete v tématu [vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: použít s `--layout` Příprava offline instalace mezipaměti pomocí balíčků prostředků se zadaným jazyk(y). Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: jeden nebo více úloh nebo ID komponenty pro přidání. Ale ne doporučené a volitelné komponenty jsou nainstalovány požadované součásti artefaktu. Můžete určit další součásti globálně pomocí `--includeRecommended` a/nebo `--includeOptional`. Pro citlivější ovládací prvek, můžete připojit `;includeRecommended` nebo `;includeOptional` ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeOptional`). Další informace najdete v tématu [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. <br/>**Poznámka:** : Pokud `--add` se používá, pouze zadané úlohy a komponenty a jejich závislosti se stáhnou. Pokud `--add` nezadáte, všechny úlohy a komponenty se stáhnou do rozložení.|
| `--includeRecommended` | **Volitelné**: obsahuje doporučené komponenty pro všechny úlohy, které jsou nainstalovány, ale nikoli volitelné komponenty. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`. |
| `--includeOptional` | **Volitelné**: obsahuje doporučené *a* volitelné komponenty pro všechny úlohy nebudou zahrnuty do rozložení. Úlohy jsou zadány s `--add`.  |
| `--keepLayoutVersion` | **Volitelné**: použít změny rozložení bez aktualizace verze rozložení. |
| `--verify` | **Volitelné**: ověřte obsah rozložení. Jsou uvedeny všechny soubory poškozen nebo chybí. |
| `--fix` | **Volitelné**: ověřte obsah rozložení.  Pokud jsou některé soubory poškozeny nebo chybí, jsou znovu staženy. Přístup k Internetu je potřeba opravit rozložení. |
| `--clean <one or more paths to catalogs>` | **Volitelné**: Odebere staré verze komponent z rozložení, které bylo aktualizováno na novější verzi. |

| **Možnosti rozšířené instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu pro instanci k instalaci. To je vyžadováno pro příkaz Install a ignoruje se pro ostatní příkazy, pokud je zadána `--installPath`. |
| `--channelUri <uri>` | **Volitelné**: identifikátor URI manifest kanálu. Pokud aktualizace nepřejete, `--channelUri` může ukazovat na neexistující soubor (například--parametr channeluri C:\doesntExist.chman). Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installChannelUri <uri>` | **Volitelné**: identifikátor URI manifestu kanálu pro instalaci. Určený identifikátor URI `--channelUri` (který musí být zadán při `--installChannelUri` určena) slouží ke zjištění aktualizací. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--installCatalogUri <uri>` | **Volitelné**: identifikátor URI manifestu katalogu pro instalaci. Je-li zadána, Správce kanálu se pokusí stáhnout manifest katalogu z tohoto identifikátoru URI před použitím tohoto identifikátoru URI v manifestu kanálu instalace. Tento parametr se používá pro podporu offline instalace, ve kterém se vytvoří mezipaměť rozložení s katalog produktů, které jsou staženy. Dá se použít pro příkaz Install. pro ostatní příkazy se ignoruje. |
| `--productId <id>` | **Volitelné** ID produktu pro instanci, která se nainstaluje. Toto je předem vyplněné za normálních podmínek instalace. |
| `--wait` | **Volitelné**: proces budou čekat na dokončení instalace před vrácením ukončovací kód. To je užitečné, když automatizace instalace, ve kterém musí jeden čekání na instalaci pro dokončení zpracování návratový kód od instalace. |
| `--locale <language-locale>` | **Volitelné**: změňte jazyk zobrazení uživatelského rozhraní pro samotný instalační služby. Nastavení budou zachována. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--cache` | **Volitelné**: Pokud je k dispozici, budou po instalaci pro další opravy zachovány balíčky. Tím se přepíše nastavení pro následné nainstaluje, opraví nebo úpravy globální zásady. Výchozí zásada je do mezipaměti balíčků. To se ignoruje pro příkaz odinstalovat. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `--nocache` | **Volitelné**: Pokud je k dispozici, balíčky budou po instalaci nebo opravě odstraněny. Budou staženy znovu pouze v případě potřeby a znovu odstraněny po použití. Tím se přepíše nastavení pro následné nainstaluje, opraví nebo úpravy globální zásady. Výchozí zásada je do mezipaměti balíčků. To se ignoruje pro příkaz odinstalovat. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `--noUpdateInstaller` | **Volitelné**: Pokud je k dispozici, brání instalačnímu programu v aktualizaci, pokud je určena tichá aktualizace. Instalační program příkaz selže a vrátí nenulový ukončovací kód, pokud noUpdateInstaller je zadána s quiet, když se vyžaduje se aktualizace instalačního programu. |
| `--noWeb` | **Volitelné**: Pokud je k dispozici, instalační program sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdařila.  Další informace najdete v tématu [nasazení z instalace v síti](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité**: Tento přepínač neukončí instalaci sady Visual Studio ze zjišťování aktualizací. Další informace najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md). **Novinka v 16.3.5**: Tento přepínač zabraňuje chybám a zvyšuje výkon při offline instalacích a aktualizacích.|
| `--path <name>=<path>` | **Volitelné**: slouží k zadání vlastních instalačních cest pro instalaci. Podporované cesty, které jsou sdíleny názvy, mezipaměť a instalace. |
| `--path cache=<path>` | **Volitelné**: používá umístění, které zadáte ke stažení instalačních souborů. Toto umístění lze nastavit pouze při prvním je nainstalována aplikace Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Volitelné**: obsahuje sdílené soubory pro souběžné instalace sady Visual Studio. Některé nástroje a sady SDK nainstalovat do umístění na této jednotce, zatímco jiné můžou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: To lze nastavit pouze jednou a na prvním je nainstalována aplikace Visual Studio. |
| `--path install=<path>` | **Volitelné**: ekvivalent `–-installPath`. Konkrétně `--installPath "C:\VS"` a `--path install="C:\VS"` jsou ekvivalentní. V jednom okamžiku lze použít pouze jeden z těchto příkazů. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Seznam ID pracovního vytížení a komponenta ID

Seznam úloh a ID komponent seřazených podle produktu Visual Studio najdete na stránce s [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md) .

## <a name="list-of-language-locales"></a>Seznam národních prostředí jazyka

| **Jazyk národního prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| Cs-cz | Čeština |
| De-de | Němčina |
| En-us | angličtina |
| ES-es | Španělština |
| Fr-fr | Francouzština |
| IT-it | Italština |
| Ja-jp | Japonština |
| Ko-kr | Korejština |
| PL-pl | Polština |
| pt-br | Portugalština – Brazílie |
| Ru-ru | Ruština |
| TR-tr | Turečtina |
| Zh-cn | Čínština (zjednodušená) |
| Zh-tw | Čínština (tradiční) |

## <a name="error-codes"></a>Kódy chyb

V závislosti na výsledek operace `%ERRORLEVEL%` proměnnou prostředí je nastavená na jednu z následujících hodnot:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Každá operace vygeneruje několik souborů protokolu v `%TEMP%` adresáře, které označují průběh instalace. Řadit podle data složce a vyhledat soubory, které začínají `dd_bootstrapper`, `dd_client`, a `dd_setup` pro zaváděcí nástroj, instalační program aplikace a nastavení modulu, v uvedeném pořadí.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

- [Příklady parametrů příkazového řádku pro instalaci sady Visual Studio](command-line-parameter-examples.md)
- [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizace instalace sady Visual Studio souborem odpovědí](automated-installation-with-response-file.md)
- [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
