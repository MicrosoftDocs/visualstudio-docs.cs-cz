---
title: Šablona projektu cloudové služby Azure pro Python
description: Visual Studio poskytuje šablony pro cloudové služby Azure napsané v Pythonu, včetně nasazení rolí, závislostí a řešení potíží.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 4d205ee2bbc0a6e9c44c34f3b0487abb4f22283e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72983666"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty cloudových služeb Azure pro Python

Visual Studio poskytuje šablony, které vám pomůžou začít vytvářet Cloudové služby Azure pomocí Pythonu.

[Cloudová služba](/azure/cloud-services/) se skládá z libovolného počtu *rolí pracovních a* *webových rolí*, z nichž každá provádí koncepčně samostatnou úlohu, ale může být samostatně replikována mezi virtuálními počítači podle potřeby pro škálování. Webové role poskytují hostování pro front-endové webové aplikace. Pokud jde o Python, jakýkoli webový rámec, který podporuje WSGI, lze použít k napsání takové aplikace (jak je podporováno [šablonou webového projektu](python-web-application-project-templates.md)). Role pracovního procesu jsou určeny pro dlouhotrvající procesy, které nekomunikují přímo s uživateli. Obvykle využívají balíčky v rámci balíčku "azure", který [`pip install azure`](https://pypi.org/project/azure)je nainstalován s .

Tento článek obsahuje podrobnosti o šabloně projektu a další podporu v sadě Visual Studio 2017 a novější (starší verze jsou podobné, ale s určitými rozdíly). Další informace o práci s Azure z Pythonu najdete v [Centru pro vývojáře Azure Pythonu](/azure/python/).

## <a name="create-a-project"></a>Vytvoření projektu

1. Nainstalujte [sadu Azure .NET SDK pro Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), která je vyžadována k použití šablony cloudové služby.
1. Ve Visual Studiu vyberte **File** > **New** > **Project**, pak vyhledejte "Azure Python" a ze seznamu vyberte Azure **Cloud Service:**

    ![Šablona projektu Azure Cloud pro Python](media/template-azure-cloud-project.png)

1. Vyberte jednu nebo více rolí, které chcete zahrnout. Cloudové projekty mohou kombinovat role napsané v různých jazycích, takže můžete snadno psát každou část aplikace v nejvhodnějším jazyce. Chcete-li do projektu po dokončení tohoto dialogového okna přidat nové role, klepněte v **Průzkumníku řešení** pravým **tlačítkem** myši na role a vyberte jednu z položek v části **Přidat**.

    ![Přidání rolí v šabloně Azure Cloud Project](media/template-azure-cloud-service-project-wizard.png)

1. Při vytváření jednotlivých projektů rolí můžete být vyzváni k instalaci dalších balíčků Pythonu, jako jsou architektury Django, Bottle nebo Flask, pokud jste vybrali roli, která používá jeden z nich.

1. Po přidání nové role do projektu se zobrazí pokyny ke konfiguraci. Změny konfigurace jsou obvykle zbytečné, ale mohou být užitečné pro budoucí přizpůsobení projektů. Všimněte si, že při přidávání více rolí současně zůstávají otevřené pouze pokyny pro poslední roli. Pokyny a tipy pro řešení potíží pro ostatní role však můžete najít v příslušných souborech *readme.mht,* které jsou umístěny buď v kořenovém adresáři role, nebo ve složce *přihrádky.*

1. Složka *přihrádky* projektu také obsahuje jeden nebo dva skripty prostředí PowerShell, které se používají ke konfiguraci vzdáleného virtuálního počítače, včetně instalace Pythonu, všech souborů [*requirements.txt*](#dependencies) v projektu a v případě potřeby nastavení služby IIS. Tyto soubory můžete upravit podle potřeby pro vaše nasazení, i když většinu běžných možností lze spravovat jinými způsoby (viz [Konfigurace nasazení role](#configure-role-deployment) níže). Nedoporučujeme odstranění těchto souborů, jako starší konfigurační skript se používá místo toho, pokud soubory nejsou k dispozici.

    ![Soubory podpory rolí pracovního procesu](media/template-azure-cloud-service-worker-role-support-files.png)

    Chcete-li přidat tyto konfigurační skripty do nového projektu, klepněte pravým tlačítkem myši na projekt, vyberte příkaz **Přidat** > **novou položku**a vyberte buď soubory podpory **webových rolí,** nebo **soubory podpory pracovních rolí**.

## <a name="configure-role-deployment"></a>Konfigurace nasazení role

Skripty prostředí PowerShell ve složce *bin* projektu role řídí nasazení této role a mohou být upraveny tak, aby přizpůsobily konfiguraci:

- *ConfigureCloudService.ps1* se používá pro webové a pracovní role, obvykle k instalaci a konfiguraci závislostí a nastavení verze Pythonu.
- *LaunchWorker.ps1* se používá pouze pro role pracovního procesu a používá se ke změně chování při spuštění, přidání argumentů příkazového řádku nebo přidání proměnných prostředí.

Oba soubory obsahují pokyny pro vlastní nastavení. Můžete také nainstalovat vlastní verzi Pythonu přidáním další úkol do hlavního projektu cloudové `PYTHON` služby *ServiceDefinition.csdef* souboru, nastavení proměnné na jeho nainstalované *python.exe* (nebo ekvivalentní) cesta. Když `PYTHON` je nastavena Python není nainstalován z NuGet.

Další konfiguraci lze provést následujícím způsobem:

1. Balíčky `pip` nainstalujte pomocí aktualizace souboru *requirements.txt* v kořenovém adresáři projektu. Skript *ConfigureCloudService.ps1* nainstaluje tento soubor při nasazení.
1. Nastavte proměnné prostředí úpravou souboru *web.config* (webových rolí) nebo `Runtime` části souboru *ServiceDefinition.csdef* (role pracovního procesu).
1. Zadejte skript a argumenty, které se mají použít pro `Runtime/EntryPoint` roli pracovního procesu, úpravou příkazového řádku v části souboru *ServiceDefinitions.csdef.*
1. Nastavte hlavní skript obslužné rutiny pro webovou roli prostřednictvím souboru *web.config.*

## <a name="test-role-deployment"></a>Testovací nasazení role

Při psaní rolí můžete testovat cloudový projekt místně pomocí emulátoru cloudové služby. Emulátor je součástí nástrojů Azure SDK a je omezená verze prostředí používaného při publikování cloudové služby do Azure.

Chcete-li spustit emulátor, nejprve se ujistěte, že váš cloudový projekt je projekt spuštění ve vašem řešení kliknutím pravým tlačítkem myši a výběrem **možnosti Nastavit jako spouštěcí projekt**. Pak vyberte **Ladění** > **start ladění** (**F5**) nebo **Ladění** > **Start bez ladění** (**Ctrl**+**F5**).

Všimněte si, že z důvodu omezení v emulátoru není možné ladit kód Pythonu. Proto doporučujeme ladit role jejich spuštěním nezávisle a potom použít emulátor pro testování integrace před publikováním.

## <a name="deploy-a-role"></a>Nasazení role

Chcete-li otevřít Průvodce **publikováním,** vyberte projekt role v **Průzkumníku řešení** a**v** hlavní nabídce vyberte **Publikovat** > nebo klepněte pravým tlačítkem myši na projekt a vyberte **publikovat**.

Proces publikování zahrnuje dvě fáze. Nejprve Visual Studio vytvoří jeden balíček obsahující všechny role pro cloudovou službu. Tento balíček je to, co se nasadí do Azure, který inicializuje jeden nebo více virtuálních počítačů pro každou roli a nasazuje zdroj.

Když se každý virtuální počítač aktivuje, spustí skript *ConfigureCloudService.ps1* a nainstaluje všechny závislosti. Tento skript ve výchozím nastavení nainstaluje nejnovější verzi Pythonu z [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) a všechny balíčky zadané v souboru *requirements.txt.*

Nakonec role pracovního procesu spustit *LaunchWorker.ps1*, který spustí skript Pythonu; webové role inicializují službu IIS a začínají zpracovávat webové požadavky.

## <a name="dependencies"></a>Závislosti

V cloudových službách používá `pip` skript *ConfigureCloudService.ps1* k instalaci sady závislostí Pythonu. Závislosti by měly být zadány v souboru s názvem *requirements.txt* (přizpůsobitelné úpravou *ConfigureCloudService.ps1*). Soubor je spuštěn `pip install -r requirements.txt` s jako součást inicializace.

Všimněte si, že instance cloudových služeb neobsahují kompilátory Jazyka C, takže všechny knihovny s rozšířeními Jazyka C musí poskytovat předkompilované binární soubory.

pip a jeho závislosti, stejně jako balíčky v *requirements.txt*, se stahují automaticky a mohou se počítat jako zpoplatněné využití šířky pásma. Podrobnosti o správě souborů *requirements.txt* naleznete v tématu [Správa požadovaných balíčků.](managing-required-packages-with-requirements-txt.md)

## <a name="troubleshooting"></a>Řešení potíží

Pokud se vaše role webu nebo pracovního procesu po nasazení nechová správně, zkontrolujte následující:

- Projekt Pythonu obsahuje složku *přihrádky\\ * s (alespoň):

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (pro role pracovního procesu)
  - *ps.cmd*

- Váš projekt Pythonu obsahuje soubor *requirements.txt,* který obsahuje všechny závislosti (nebo alternativně kolekci souborů kol).
- Povolte vzdálenou plochu ve své cloudové službě a prozkoumejte soubory protokolu.
- Protokoly pro *ConfigureCloudService.ps1* a *LaunchWorker.ps1* jsou uloženy v *c:\Resources\Directory\%RoleId%. DiagnosticStore\LogFiles* ve vzdáleném počítači.
- Webové role mohou zapisovat další protokoly do cesty nakonfigurované v *souboru web.config*, konkrétně na cestu v aplikaciSetting. `WSGI_LOG` Většina pravidelných Protokolování IIS nebo FastCGI funguje také.
- V současné době *launchworker.ps1.log* soubor je jediný způsob, jak zobrazit výstup nebo chyby zobrazené role pracovního procesu Pythonu.
