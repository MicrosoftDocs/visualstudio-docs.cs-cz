---
title: Šablona projektu Azure cloud service pro Python
description: Visual Studio poskytuje šablony pro Azure cloud services, které jsou napsané v Pythonu, včetně nasazení role, závislosti a řešení potíží.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 5eafbf0b24e464e81447c0677d53096032343580
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068523"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty Azure cloudových služeb pro Python

Visual Studio poskytuje šablony, které vám pomůžou začít s vytváření cloudových služeb Azure pomocí Pythonu.

A [Cloudová služba](https://docs.microsoft.com/azure/cloud-services/) se skládá z libovolného počtu *rolí pracovního procesu* a *webové role*, z nichž každý provádí koncepčně samostatné úlohy, ale můžete samostatně replikovat napříč podle potřeby škálování virtuálních počítačů. Webové role poskytují hostování pro front-endové webové aplikace. Pokud Python obavy, webová architektura, která podporuje s rozhraním WSGI můžete použít pro zapsání takové aplikace (podporuje [Šablona webového projektu](python-web-application-project-templates.md)). Role pracovního procesu jsou určené pro dlouho běžící procesy, které nemají možnost zasahovat přímo uživatelům. Obvykle využívají pomocí balíčků v rámci balíčku "azure", která se instaluje s [ `pip install azure` ](https://pypi.org/project/azure).

Tento článek obsahuje podrobnosti o šabloně projektu a další podporu v sadě Visual Studio 2017 (starší verze se podobné, ale několik rozdílů). Další informace o práci s Azure v Pythonu, přejděte [středisko pro vývojáře Python](https://docs.microsoft.com/python/azure/?view=azure-python).

## <a name="create-a-project"></a>Vytvoření projektu

1. Nainstalujte [sady Azure .NET SDK pro Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), které je potřeba použít šablona cloudové služby.
1. V sadě Visual Studio, vyberte **souboru** > **nový** > **projektu**, vyhledejte "Azure Python" a vyberte **cloudu Azure Služba** ze seznamu:

    ![Šablona projektu cloudové Azure pro Python](media/template-azure-cloud-project.png)

1. Vyberte jednu nebo víc rolí, které chcete zahrnout. Projekty cloudových může kombinovat role, které jsou napsány v různých jazycích, takže snadno můžete napsat jednotlivých součástí aplikace v jazyce nejvhodnější. Chcete-li přidat nové role do projektu po dokončení tohoto dialogového okna, klikněte pravým tlačítkem na **role** v **Průzkumníka řešení** a vyberte jednu z položek v části **přidat**.

    ![Přidání role v šabloně projektu cloudu Azure](media/template-azure-cloud-service-project-wizard.png)

1. Při vytváření projektů jednotlivé role se vám může zobrazit výzva k instalaci dalších balíčků Python, jako je například rozhraní Django, Bottle nebo Flask, pokud jste vybrali roli, která používá jedna z těchto.

1. Po přidání nové role do vašeho projektu, se zobrazí pokyny ke konfiguraci. Změny konfigurace jsou obvykle nepotřebná, ale mohou být užitečné pro budoucí přizpůsobení vašich projektů. Všimněte si, že při přidávání více rolí ve stejnou dobu, zůstanou otevřené a pokynů pro poslední role. Však můžete najít pokyny a tipy pro řešení potíží pro ostatní role v jejich *readme.mht* soubory umístěné v kořenovém adresáři role nebo v *bin* složky.

1. Projektové *bin* složka také obsahuje jeden nebo dva skripty prostředí PowerShell, které se používají ke konfiguraci vzdáleného virtuálního počítače, včetně instalace Pythonu, všechny [ *souboru requirements.txt* ](#dependencies) souborů ve vašem projektu a nastavení služby IIS v případě potřeby. Můžete kdykoli upravit podle potřeby tyto soubory do nasazení, i když je možné spravovat nejběžnější možnosti jinými způsoby (viz [konfigurace nasazení role](#configure-role-deployment) níže). Není doporučujeme odebrat tyto soubory jako skript starší verzi konfigurace se používá místo toho, pokud soubory nejsou k dispozici.

    ![Podpůrné soubory pro Role pracovního procesu](media/template-azure-cloud-service-worker-role-support-files.png)

    Chcete-li přidat tyto konfigurační skripty na nový projekt, klikněte pravým tlačítkem na projekt, vyberte **přidat** > **nová položka**a vyberte buď **soubory podpory webové Role** nebo **Podpůrné soubory pro Role pracovního procesu**.

## <a name="configure-role-deployment"></a>Konfigurace nasazení role

Powershellové skripty do projektu role *bin* složky řízení nasazení této roli a může být upraven tak přizpůsobit konfiguraci:

- *ConfigureCloudService.ps1* se používá pro webové a pracovní role, obvykle nainstalovat a nakonfigurovat závislosti a verzi Pythonu.
- *Souboru LaunchWorker.ps1* se používá pouze pro role pracovních procesů a umožňuje změnit chování při spuštění, přidejte argumenty příkazového řádku nebo přidat proměnné prostředí.

Oba soubory obsahují pokyny pro přizpůsobení. Vlastní verzi Pythonu můžete také nainstalovat tak, že přidáte jinou úlohu projekt hlavní cloudové služby *ServiceDefinition.csdef* soubor nastavení `PYTHON` proměnné pro jeho nainstalované *python.exe*(nebo obdobných) cestu. Když `PYTHON` je nastavena, z NuGet není nainstalován Python.

Další konfigurace lze provést následujícím způsobem:

1. Instalace balíčků s využitím `pip` aktualizací *souboru requirements.txt* souboru v kořenovém adresáři vašeho projektu. *ConfigureCloudService.ps1* skript nainstaluje tento soubor na nasazení.
1. Nastavení proměnných prostředí tak, že upravíte vaše *web.config* souboru (webové role) nebo `Runtime` část vaší *ServiceDefinition.csdef* souboru (role pracovního procesu).
1. Zadejte skript a argumenty, které mají použít pro roli pracovního procesu tak, že upravíte na příkazovém řádku ve `Runtime/EntryPoint` část vaší *ServiceDefinitions.csdef* souboru.
1. Nastavte hlavní obslužná rutina skriptu pro webové role prostřednictvím *web.config* souboru.

## <a name="test-role-deployment"></a>Testovací nasazení pro roli

Při zápisu role, můžete otestovat projekt cloudové místně pomocí emulátoru služby Cloud. Emulátor je součástí Azure SDK Tools a je omezená verze prostředí použité při publikování vaší cloudové služby do Azure.

Pokud chcete spustit emulátor, nejdřív zajistit projekt cloudové projekt při spuštění ve vašem řešení tak, že kliknete pravým tlačítkem a vyberete **nastavit jako spouštěný projekt**. Potom vyberte **ladění** > **spustit ladění** (**F5**) nebo **ladění** > **spustit bez Ladění** (**Ctrl**+**F5**).

Všimněte si, že z důvodu omezení se spustila v emulátoru není možné ladit kód Pythonu. Proto doporučujeme ladění role je spuštěním nezávisle a pak použít emulátor integrační testování před publikováním.

## <a name="deploy-a-role"></a>Nasazení role

Chcete-li otevřít **publikovat** průvodce, vyberte roli projektu v **Průzkumníka řešení** a vyberte **sestavení** > **publikovat** z hlavní nabídky, nebo klikněte pravým tlačítkem na projekt a vyberte **publikovat**.

Proces publikování zahrnuje dvě fáze. Nejprve Visual Studio vytvoří jeden balíček, který obsahuje všechny role pro cloudovou službu. Tento balíček je, co je nasazený do Azure, který inicializuje jednu nebo více virtuálních počítačů pro každou roli a nasadí zdroji.

Jak každý virtuální počítač se aktivuje, spustí *ConfigureCloudService.ps1* skriptu a instaluje všechny závislosti. Tento skript ve výchozím nastavení nainstaluje nejnovější verzi Pythonu z [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) a všechny balíčky podle *souboru requirements.txt* souboru.

Nakonec spuštěním rolí pracovního procesu *souboru LaunchWorker.ps1*, která spustí váš skript Python; webové role inicializace služby IIS a zahájit zpracování webových žádostí.

## <a name="dependencies"></a>Závislosti

U Cloud Services *ConfigureCloudService.ps1* skript pomocí `pip` nainstalovat sadu závislosti Pythonu. Závislosti musí být zadán v souboru s názvem *souboru requirements.txt* (přizpůsobit úpravou *ConfigureCloudService.ps1*). Soubor je spuštěn s `pip install -r requirements.txt` součástí inicializace.

Všimněte si, že instance služby cloud neobsahují kompilátory jazyka C, tak všechny knihovny se zmírněními hrozeb rozšíření C nezajistil předem zkompilované binární soubory.

PIP a jeho závislosti, jakož i balíčky v *souboru requirements.txt*, se automaticky stáhnou a může počítat jako fakturovatelná šířka pásma. V tématu [spravovat požadované balíčky](managing-required-packages-with-requirements-txt.md) podrobné informace o správě *souboru requirements.txt* soubory.

## <a name="troubleshooting"></a>Poradce při potížích

Pokud vaše webová nebo pracovní role nechoval správně po nasazení, zkontrolujte následující:

- Zahrnuje projektu v Pythonu *bin\\*  složka s (minimálně):

  - *ConfigureCloudService.ps1*
  - *Souboru LaunchWorker.ps1* (u rolí pracovního procesu)
  - *PS.cmd*

- Zahrnuje projektu v Pythonu *souboru requirements.txt* seznamu všechny závislosti (nebo případně kolekce souborů wheel) souborů.
- Povolení vzdálené plochy na cloudové služby a prozkoumejte soubory protokolu.
- Protokoly pro *ConfigureCloudService.ps1* a *souboru LaunchWorker.ps1* jsou uloženy v *C:\Resources\Directory\%RoleId %. DiagnosticStore\LogFiles* složky na vzdáleném počítači.
- Webové role může zapsat další protokoly na cestu nakonfigurované v *web.config*, a to na cestu v `WSGI_LOG` nastavení aplikace. Většině běžných protokolování služby IIS a FastCGI také funguje.
- V současné době *LaunchWorker.ps1.log* soubor je jediný způsob, jak zobrazit výstup a chyby zobrazí vaše role pracovních procesů Pythonu.
