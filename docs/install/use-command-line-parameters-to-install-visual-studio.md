---
title: Instalace sady Visual Studio s použitím parametrů příkazového řádku
titleSuffix: ''
description: Další informace o použití parametrů příkazového řádku k řízení nebo přizpůsobit instalaci sady Visual Studio.
ms.date: 09/11/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1f9e5d1dadd9caf95b8e6cb8e5fec70daf984ac9
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913248"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Instalace sady Visual Studio s použitím parametrů příkazového řádku

Při instalaci sady Visual Studio z příkazového řádku můžete použít nejrůznější parametry příkazového řádku pro řízení nebo přizpůsobení instalace. Z příkazového řádku můžete provést následující akce:

- Spusťte instalaci s možnostmi předem vybrali.
- Automatizujte proces instalace.
- Vytvoření mezipaměti (rozložení) instalačních souborů pro pozdější použití.

Možnosti příkazového řádku se používají ve spojení s zaváděcím nástrojem pro instalaci, což je malý (1 MB) soubor, který iniciuje proces stahování. Zaváděcí nástroj je první spustitelný soubor, který se spustí, když si stáhnete z webu Visual Studio. Chcete-li získat přímý odkaz na nejnovější verzi bootstrapper pro edici produktu, které chcete instalovat pomocí následujících odkazů:

::: moniker range="vs-2017"

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end

## <a name="command-line-parameters"></a>Parametry příkazového řádku

 Parametry příkazového řádku aplikace Visual Studio jsou malá a velká písmena.

> Syntaxe: `vs_enterprise.exe [command] <options>...`

Podle `vs_enterprise.exe` potřeby nahraďte produktovou edici, kterou instalujete. (Případně můžete použít `vs_installer.exe`.)

>[!TIP]
> Další příklady použití příkazového řádku k instalaci sady Visual Studio najdete na stránce s [Příklady parametrů příkazového řádku](command-line-parameter-examples.md) .

| **Příkaz** | **Popis** |
| ----------------------- | --------------- |
| (prázdné) | Nainstaluje produkt. |
| `modify` | Upraví zobrazí nainstalovaný produkt. |
| `update` | Aktualizuje zobrazí nainstalovaný produkt. |
| `repair` | Opraví zobrazí nainstalovaný produkt. |
| `uninstall` | Odinstaluje zobrazí nainstalovaný produkt. |
| `export` | **Novinka ve verzi 15,9**: Exportuje výběr instalace do konfiguračního souboru instalace. **Poznámka:** Dá se použít jenom s vs_installer. exe. |

## <a name="install-options"></a>Možnosti instalace

| **Možnost instalace** | **Popis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Instalační adresář pro instance, kterou chcete použít. Pro instalačního příkazu, to je **volitelné** a nainstalovanou instanci. Pro další příkazy jde **vyžaduje** a kam se nainstaloval dříve nainstalovanou instanci. |
| `--addProductLang <language-locale>` | **Volitelné**: Během operace instalace nebo změny určuje jazykové sady uživatelského rozhraní, které jsou nainstalovány na produkt. Může se objevit více než jednou v příkazovém řádku, chcete-li přidat více jazykových sad. Pokud není k dispozici, instalace používá národní prostředí počítače. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--removeProductLang <language-locale>` | **Volitelné**: Během operace instalace nebo změny určuje jazykové sady uživatelského rozhraní, které se mají z produktu odebrat. Může se objevit více než jednou v příkazovém řádku, chcete-li přidat více jazykových sad. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: Jedno nebo více úloh nebo ID součástí, které chcete přidat. Ale ne doporučené a volitelné komponenty jsou nainstalovány požadované součásti artefaktu. Můžete určit další součásti globálně pomocí `--includeRecommended` a/nebo `--includeOptional`. Chcete-li zahrnout více úloh nebo komponenty, opakujte `--add` příkazu (například `--add Workload1 --add Workload2`). Pro citlivější ovládací prvek, můžete připojit `;includeRecommended` nebo `;includeOptional` ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeRecommended;includeOptional`). Další informace najdete v tématu [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. Tato možnost podle potřeby, můžete opakovat.|
| `--remove <one or more workload or component IDs>` | **Volitelné**: Jedno nebo více úloh nebo ID součástí, které chcete odebrat. Další informace najdete v tématu naše [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. Tato možnost podle potřeby, můžete opakovat.|
| `--in <path>` | **Volitelné**: Identifikátor URI nebo cesta k souboru odpovědí.  |
| `--all` | **Volitelné**: Bez ohledu na to, jestli se mají nainstalovat všechny úlohy a součásti produktu |
| `--allWorkloads` | **Volitelné**: Nainstaluje všechny úlohy a součásti bez doporučených nebo volitelných součástí. |
| `--includeRecommended` | **Volitelné**: Zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`. |
| `--includeOptional` | **Volitelné**: Zahrnuje volitelné součásti pro všechny nainstalované úlohy, ale ne Doporučené součásti. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`.  |
| `--quiet, -q` | **Volitelné**: Při instalaci nezobrazit žádné uživatelské rozhraní. |
| `--passive, -p` | **Volitelné**: Zobrazí uživatelské rozhraní, ale nepožaduje žádné interakce od uživatele. |
| `--norestart` | **Volitelné**: Pokud je k dispozici `--passive` , `--quiet` příkazy s nebo nebudou automaticky restartovat počítač (v případě potřeby).  To je ignorováno, pokud žádná `--passive` ani `--quiet` jsou uvedeny.  |
| `--nickname <name>` | **Volitelné**: Tím se definuje Přezdívka, která se přiřadí nainstalovanému produktu. Přezdívka nesmí být delší než 10 znaků.  |
| `--productKey` | **Volitelné**: Tím se definuje kód Product Key, který se má použít pro nainstalovaný produkt. Skládá se z 25 alfanumerických znaků buď ve formátu `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` nebo `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Zobrazte offline verzi této stránky. |
| `--config <path>` | **Volitelné** a **nové v 15,9**: Během operace instalace nebo úprav se tím určují úlohy a komponenty, které se mají přidat, na základě dříve uloženého konfiguračního souboru instalace. Tato operace je additive a nedojde k odebrání jakékoli úlohy nebo komponenty, pokud nejsou k dispozici v souboru. Navíc nepřidá položky, které se nevztahují na produkt. Během operace exportu určuje umístění pro uložení konfigurační soubor instalace. |

> [!IMPORTANT]
> Při zadávání více úloh a součástí je třeba pro každou položku zopakovat `--add` přepínač `--remove` příkazového řádku nebo.

## <a name="layout-options"></a>Možnosti rozložení

| **Možnosti rozložení** | **Popis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Určuje adresář, který chcete vytvořit offline instalaci mezipaměti. Další informace najdete v tématu [vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Volitelné**: Používá se `--layout` s pro přípravu offline mezipaměti instalace s balíčky prostředků se zadanými jazyky. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--add <one or more workload or component IDs>` | **Volitelné**: Jedno nebo více úloh nebo ID součástí, které chcete přidat. Ale ne doporučené a volitelné komponenty jsou nainstalovány požadované součásti artefaktu. Můžete určit další součásti globálně pomocí `--includeRecommended` a/nebo `--includeOptional`. Pro citlivější ovládací prvek, můžete připojit `;includeRecommended` nebo `;includeOptional` ID (například `--add Workload1;includeRecommended` nebo `--add Workload2;includeOptional`). Další informace najdete v tématu [pracovního vytížení a komponenta ID](workload-and-component-ids.md) stránky. <br/>**Poznámka:** Pokud `--add` se používá, stáhnou se jenom zadané úlohy a komponenty a jejich závislosti. Pokud `--add` neurčíte, všechny úlohy a komponenty se stáhnou do rozložení.|
| `--includeRecommended` | **Volitelné**: Zahrnuje Doporučené součásti pro všechny nainstalované úlohy, ale ne volitelné součásti. Úlohy jsou zadány buď pomocí `--allWorkloads` nebo `--add`. |
| `--includeOptional` | **Volitelné**: Obsahuje doporučené *a* volitelné komponenty pro všechny úlohy, které jsou součástí rozložení. Úlohy jsou zadány s `--add`.  |
| `--keepLayoutVersion` | **Novinka v 15,3, volitelné**: Aplikuje změny rozložení bez aktualizace verze rozložení. |
| `--verify` | **Novinka v 15,3, volitelné**: Ověřte obsah rozložení. Jsou uvedeny všechny soubory poškozen nebo chybí. |
| `--fix` | **Novinka v 15,3, volitelné**: Ověřte obsah rozložení.  Pokud nejsou nalezeny žádné soubory je poškozený nebo chybí, že jsou znovu staženy. Přístup k Internetu je potřeba opravit rozložení. |
| `--clean <one or more paths to catalogs>` | **Novinka v 15,3, volitelné**: Odebere staré verze komponent z rozložení, které bylo aktualizováno na novější verzi. |

| **Možnosti rozšířené instalace** | **Popis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Volitelné**: ID kanálu, který má být nainstalován. Toto je nezbytné instalační příkaz ignorován pro další příkazy `--installPath` je zadán. |
| `--channelUri <uri>` | **Volitelné**: Identifikátor URI manifestu kanálu. Pokud nejsou aktualizace žádoucí, `--channelUri` může odkazovat na neexistující soubor (například--parametr channeluri C:\doesntExist.chman). To je možné pro příkaz install; u ostatních příkazů se ignoruje. |
| `--installChannelUri <uri>` | **Volitelné**: Identifikátor URI manifestu kanálu, který se má použít pro instalaci. Určený identifikátor URI `--channelUri` (který musí být zadán při `--installChannelUri` určena) slouží ke zjištění aktualizací. To je možné pro příkaz install; u ostatních příkazů se ignoruje. |
| `--installCatalogUri <uri>` | **Volitelné**: Identifikátor URI manifestu katalogu, který se má použít pro instalaci. Je-li zadána, Správce kanálu se pokusí stáhnout manifest katalogu z tohoto identifikátoru URI před použitím tohoto identifikátoru URI v manifestu kanálu instalace. Tento parametr se používá pro podporu offline instalace, ve kterém se vytvoří mezipaměť rozložení s katalog produktů, které jsou staženy. To je možné pro příkaz install; u ostatních příkazů se ignoruje. |
| `--productId <id>` | **Volitelné** ID produktu pro instanci, která se nainstaluje. To je předem v běžných podmínek instalace. |
| `--wait` | **Volitelné**: Před vrácením ukončovacího kódu bude proces čekat na dokončení instalace. To je užitečné, když automatizace instalace, ve kterém musí jeden čekání na instalaci pro dokončení zpracování návratový kód od instalace. |
| `--locale <language-locale>` | **Volitelné**: Změňte jazyk zobrazení uživatelského rozhraní pro samotný instalační program. Nastavení budou zachována. Další informace najdete v tématu [seznam národních prostředí jazyka](#list-of-language-locales) části na této stránce.|
| `--cache` | **Novinka v 15,2, volitelné**: Pokud je tato akce k dispozici, budou balíčky po instalaci pro další opravy zachovány. Tím se přepíše nastavení pro následné nainstaluje, opraví nebo úpravy globální zásady. Výchozí zásada je do mezipaměti balíčků. To se ignoruje pro příkaz odinstalovat. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `--nocache` | **Novinka v 15,2, volitelné**: Pokud je k dispozici, balíčky budou po instalaci nebo opravě odstraněny. Že se znovu stáhnou pouze v případě potřeby a znovu po použití odstraněna. Tím se přepíše nastavení pro následné nainstaluje, opraví nebo úpravy globální zásady. Výchozí zásada je do mezipaměti balíčků. To se ignoruje pro příkaz odinstalovat. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `--noUpdateInstaller` | **Novinka v 15,2, volitelné**: Pokud je k dispozici, brání instalačnímu programu v aktualizaci, pokud je určena tichá aktualizace. Instalační program příkaz selže a vrátí nenulový ukončovací kód, pokud noUpdateInstaller je zadána s quiet, když se vyžaduje se aktualizace instalačního programu. |
| `--noWeb` | **Novinka v 15,3, volitelné**: Pokud je k dispozici, instalační program sady Visual Studio používá soubory v adresáři rozložení k instalaci sady Visual Studio. Pokud se uživatel pokusí nainstalovat součásti, které nejsou v rozložení, instalace se nezdařila.  Další informace najdete v tématu [nasazení z instalace v síti](create-a-network-installation-of-visual-studio.md). <br/><br/> **Důležité**informace: Tento přepínač neukončí instalaci sady Visual Studio z vyhledávání aktualizací. Další informace najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **Novinka v 15,7, volitelné**: Slouží k zadání vlastních instalačních cest pro instalaci. Podporované cesty, které jsou sdíleny názvy, mezipaměť a instalace. |
| `--path cache=<path>` | **Novinka v 15,7, volitelné**: Použije umístění, které zadáte ke stažení instalačních souborů. Toto umístění lze nastavit pouze při prvním je nainstalována aplikace Visual Studio. Příklad: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novinka v 15,7, volitelné**: Obsahuje sdílené soubory pro souběžné instalace sady Visual Studio. Některé nástroje a sady SDK nainstalovat do umístění na této jednotce, zatímco jiné můžou toto nastavení přepsat a nainstalovat na jinou jednotku. Příklad: `--path shared="C:\VS\shared"` <br><br>Důležité: Tuto možnost lze nastavit pouze jednou a při prvním instalaci sady Visual Studio. |
| `--path install=<path>` | **Novinka v 15,7, volitelné**: `–-installPath`Ekvivalent. Konkrétně `--installPath "C:\VS"` a `--path install="C:\VS"` jsou ekvivalentní. Pouze jeden z nich je možné najednou. |

## <a name="list-of-workload-ids-and-component-ids"></a>Seznam ID pracovního vytížení a komponenta ID

Seznam úloh a ID komponent seřazených podle produktu Visual Studio najdete na stránce s [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md) .

## <a name="list-of-language-locales"></a>Seznam národních prostředí jazyka

| **Jazyk národního prostředí** | **Jazyk** |
| ----------------------- | --------------- |
| Cs-cz | Čeština |
| De-de | Němčina |
| En-us | Angličtina |
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
