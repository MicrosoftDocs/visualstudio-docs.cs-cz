---
title: Šablona projektu cloudové služby Azure pro Python
description: Visual Studio poskytuje šablony pro cloudové služby Azure napsané v Pythonu, včetně nasazení rolí, závislostí a řešení potíží.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: a40745b19bde57f7f0ca52e04a11a89ad1ca69ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912429"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty cloudových služeb Azure pro Python

Visual Studio poskytuje šablony, které vám pomůžou začít vytvářet Cloud Services Azure pomocí Pythonu.

[Cloudová služba](/azure/cloud-services/) se skládá z libovolného počtu *rolí pracovních procesů* a *webových rolí*, z nichž každý provádí koncepční samostatnou úlohu, ale je možné ji samostatně replikovat mezi virtuálními počítači podle potřeby pro škálování. Webové role poskytují hostování pro webové aplikace front-endu. Tam, kde je to Python, může být jakékoli webové rozhraní, které podporuje rozhraním WSGI, použito k zápisu takové aplikace (podporované [šablonou webového projektu](python-web-application-project-templates.md)). Role pracovního procesu jsou určené pro dlouhotrvající procesy, které nekomunikují přímo s uživateli. Typicky využívají balíčky v rámci balíčku Azure, který je nainstalovaný s nástrojem [`pip install azure`](https://pypi.org/project/azure) .

Tento článek obsahuje podrobné informace o šabloně projektu a další podporu v aplikaci Visual Studio 2017 a novějších verzích (starší verze jsou podobné, ale s některými rozdíly). Další informace o práci s Azure z Pythonu najdete v [centru pro vývojáře v Pythonu pro Azure](/azure/python/).

## <a name="create-a-project"></a>Vytvoření projektu

1. Nainstalujte [sadu Azure .NET SDK pro Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), která je nutná k použití šablony cloudové služby.
1. V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**, vyhledejte "Azure Python" a v seznamu vyberte **cloudovou službu Azure** :

    ![Šablona cloudového projektu Azure pro Python](media/template-azure-cloud-project.png)

1. Vyberte jednu nebo více rolí, které chcete zahrnout. Cloudové projekty mohou kombinovat role napsané v různých jazycích, takže můžete snadno napsat každou část aplikace do nejvhodnějšího jazyka. Chcete-li po dokončení tohoto dialogu Přidat nové role do projektu, klikněte pravým tlačítkem na **role** v **Průzkumník řešení** a vyberte jednu z položek v části **Přidat**.

    ![Přidání rolí do šablony cloudového projektu Azure](media/template-azure-cloud-service-project-wizard.png)

1. Při vytváření projektů jednotlivých rolí se může zobrazit výzva k instalaci dalších balíčků Pythonu, jako jsou Django, láhev nebo reakční prostředí, pokud jste vybrali roli, která používá jeden z nich.

1. Po přidání nové role do projektu se zobrazí pokyny ke konfiguraci. Změny konfigurace jsou obvykle zbytečné, ale mohou být užitečné pro budoucí přizpůsobení vašich projektů. Všimněte si, že při přidávání více rolí současně budou otevřené jenom pokyny pro poslední roli. Pokyny a tipy pro řešení potíží pro ostatní role ale můžete najít v příslušných souborech *Readme. MHT* , které jsou umístěné v kořenovém adresáři role nebo ve složce *bin* .

1. Složka *bin* projektu obsahuje také jeden nebo dva skripty prostředí PowerShell, které se používají ke konfiguraci vzdáleného virtuálního počítače, včetně instalace Pythonu, jakéhokoli [*requirements.txt*](#dependencies) souboru v projektu a nastavení služby IIS v případě potřeby. Tyto soubory můžete upravit podle potřeby nasazení, i když většinu běžných možností můžete spravovat jinými způsoby (viz [Konfigurace nasazení rolí](#configure-role-deployment) níže). Nedoporučujeme tyto soubory odebrat, protože se místo nich používá starší konfigurační skript, pokud nejsou soubory k dispozici.

    ![Podpůrné soubory role pracovního procesu](media/template-azure-cloud-service-worker-role-support-files.png)

    Chcete-li přidat tyto konfigurační skripty do nového projektu, klikněte pravým tlačítkem myši na projekt, vyberte možnost **Přidat**  >  **novou položku** a vyberte možnost soubory **podpory webové role** nebo **podpůrné soubory role pracovního procesu**.

## <a name="configure-role-deployment"></a>Konfigurace nasazení role

Skripty PowerShellu ve složce *bin* projektu role určují nasazení této role a dají se upravit pro přizpůsobení konfigurace:

- *ConfigureCloudService.ps1* se používá pro webové a pracovní role, většinou pro instalaci a konfiguraci závislostí a nastavení verze Pythonu.
- *LaunchWorker.ps1* se používá pouze pro role pracovního procesu a slouží ke změně chování při spuštění, přidání argumentů příkazového řádku nebo přidání proměnných prostředí.

Oba soubory obsahují pokyny pro přizpůsobení. Můžete také nainstalovat vlastní verzi Pythonu přidáním další úlohy do souboru *ServiceDefinition. csdef* projektu hlavní cloudové služby, nastavením `PYTHON` proměnné na její instalovanou *python.exe* (nebo ekvivalentní) cestu. Když `PYTHON` je nastavená, Python není nainstalovaný z NuGet.

Další konfiguraci lze provést následujícím způsobem:

1. Nainstalujte balíčky pomocí `pip` aktualizace souboru *requirements.txt* v kořenovém adresáři vašeho projektu. Skript *ConfigureCloudService.ps1* nainstaluje tento soubor na nasazení.
1. Nastavte proměnné prostředí úpravou souboru *web.config* (webové role) nebo `Runtime` části souboru *ServiceDefinition. csdef* (role pracovních procesů).
1. Určete skript a argumenty, které se mají použít pro roli pracovního procesu, úpravou příkazového řádku v `Runtime/EntryPoint` části souboru *ServiceDefinitions. csdef* .
1. Nastavte hlavní skript obslužné rutiny pro webovou roli prostřednictvím souboru *web.config* .

## <a name="test-role-deployment"></a>Nasazení testovací role

Při psaní vašich rolí můžete cloudový projekt otestovat místně pomocí emulátoru cloudové služby. Emulátor je součástí Azure SDK Tools a jedná se o omezené verze prostředí používaného při publikování cloudové služby do Azure.

Chcete-li spustit emulátor, nejprve zajistěte, aby váš cloudový projekt byl projekt po spuštění ve vašem řešení kliknutím pravým tlačítkem a výběrem možnosti **nastavit jako spouštěný projekt**. Pak vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo **ladění**  >  **Spusťte bez ladění** (**CTRL** + **F5**).

Všimněte si, že kvůli omezením v emulátoru není možné ladit kód Pythonu. Doporučujeme vám ladit role jejich spouštěním nezávisle a potom použít emulátor pro testování integrace před publikováním.

## <a name="deploy-a-role"></a>Nasazení role

Chcete-li otevřít průvodce **publikováním** , vyberte projekt role v **Průzkumník řešení** a v hlavní nabídce vyberte **sestavení**  >  **publikovat** , nebo klikněte pravým tlačítkem myši na projekt a vyberte **publikovat**.

Proces publikování zahrnuje dvě fáze. Nejprve sada Visual Studio vytvoří jeden balíček obsahující všechny role pro vaši cloudovou službu. Tento balíček je nasazený do Azure, který inicializuje jeden nebo víc virtuálních počítačů pro každou roli a nasadí zdroj.

Při aktivaci každého virtuálního počítače se spustí skript *ConfigureCloudService.ps1* a nainstaluje všechny závislosti. Tento skript ve výchozím nastavení nainstaluje nejnovější verzi Pythonu z [nugetu](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) a všechny balíčky zadané v souboru *requirements.txt* .

Role pracovního procesu se spustí *LaunchWorker.ps1*, ve kterém se spouští váš skript Pythonu. webové role inicializují službu IIS a začnou zpracovávat webové požadavky.

## <a name="dependencies"></a>Závislosti

Pro Cloud Services skript *ConfigureCloudService.ps1* používá `pip` k instalaci sady závislostí Pythonu. Závislosti by měly být zadány v souboru s názvem *requirements.txt* (lze přizpůsobit úpravou *ConfigureCloudService.ps1*). Soubor se spustí v rámci `pip install -r requirements.txt` inicializace.

Všimněte si, že instance cloudové služby neobsahují kompilátory jazyka C, takže všechny knihovny s rozšířeními jazyka C musí poskytovat předem zkompilované binární soubory.

PIP a jeho závislosti a balíčky v *requirements.txt* se automaticky stahují a můžou se počítat jako Fakturovatelné využití šířky pásma. Podrobnosti o správě *requirements.txt* souborů najdete v tématu [Správa požadovaných balíčků](managing-required-packages-with-requirements-txt.md) .

## <a name="troubleshooting"></a>Řešení potíží

Pokud vaše webová role nebo role pracovního procesu po nasazení správně nefunguje, podívejte se na následující:

- Váš projekt Pythonu obsahuje *složku \\ bin* s (aspoň):

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (pro role pracovního procesu)
  - *ps.cmd*

- Váš projekt v Pythonu obsahuje *requirements.txt* soubor se seznamem všech závislostí (nebo alternativně kolekce souborů kol).
- Povolte na cloudové službě Vzdálená plocha a prozkoumejte soubory protokolů.
- Protokoly pro *ConfigureCloudService.ps1* a *LaunchWorker.ps1* jsou uloženy v *C:\Resources\Directory \% RoleId%. DiagnosticStore\LogFiles* složka na vzdáleném počítači.
- Webové role můžou zapisovat další protokoly do cesty nakonfigurované v *web.config*, konkrétně na cestu v `WSGI_LOG` AppSetting. Nejčastěji se používá služba IIS nebo protokolování FastCGI.
- V současné době je soubor *LaunchWorker.ps1. log* jediným způsobem, jak zobrazit výstup nebo chyby zobrazené vaší rolí pracovního procesu Pythonu.
