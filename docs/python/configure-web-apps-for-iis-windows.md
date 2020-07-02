---
title: Konfigurace webových aplikací v Pythonu pro službu IIS
description: Jak nakonfigurovat webové aplikace v Pythonu, aby se spouštěly pomocí Internetová informační služba z virtuálního počítače s Windows
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 3c756f3d9a89294ecce054650037be3f7b26c291
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540930"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurace webových aplikací v Pythonu pro službu IIS

Při použití Internetová informační služba (IIS) jako webového serveru na počítači s Windows (včetně [virtuálních počítačů s Windows v Azure](/azure/architecture/reference-architectures/n-tier/windows-vm)musí aplikace Python zahrnovat specifická nastavení do jejich *web.config* souborů, aby mohla služba IIS správně zpracovat kód v Pythonu. V samotném počítači musí být také nainstalovaný Python spolu se všemi balíčky, které webová aplikace vyžaduje.

> [!Note]
> V tomto článku najdete dřív uvedené pokyny ke konfiguraci Pythonu na Azure App Service ve Windows. Rozšíření Pythonu a hostitelé systému Windows používané v tomto scénáři se už nepoužívají ve prospěch Azure App Service v systému Linux. Další informace najdete v tématu [publikování aplikací v Pythonu do Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Předchozí článek je však stále k dispozici pro [správu App Service ve Windows s rozšířeními Pythonu](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Instalace Pythonu ve Windows

Pokud chcete spustit webovou aplikaci, nejdřív nainstalujte požadovanou verzi Pythonu přímo na hostitelský počítač s Windows, jak je popsáno v tématu [instalace překladačů Pythonu](installing-python-interpreters.md).

Zaznamenejte umístění `python.exe` překladače pro pozdější kroky. Pro usnadnění můžete přidat toto umístění do proměnné prostředí PATH.

## <a name="install-packages"></a>Nainstalovat balíčky

Při použití vyhrazeného hostitele můžete použít globální prostředí Python ke spuštění vaší aplikace místo virtuálního prostředí. Proto můžete všechny požadavky vaší aplikace nainstalovat do globálního prostředí pouhým spuštěním `pip install -r requirements.txt` na příkazovém řádku.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Nastavit web.config, aby odkazovaly na interpret Pythonu

Soubor *web.config* vaší aplikace dává pokyn webovému serveru služby IIS (7 +), který běží ve Windows, o tom, jak by měl zpracovávat požadavky Pythonu prostřednictvím HttpPlatform (doporučeno) nebo FastCGI. Sady Visual Studio verze 2015 a novější provádí tyto úpravy automaticky. Při použití sady Visual Studio 2017 a novější je nutné upravit *web.config* ručně.

### <a name="configure-the-httpplatform-handler"></a>Konfigurace obslužné rutiny HttpPlatform

Modul HttpPlatform předá připojení soketů přímo k samostatnému procesu Pythonu. Tato předávací rutina umožňuje spustit libovolný webový server, který chcete, ale vyžaduje spouštěcí skript, který spouští místní webový server. Zadáte skript v `<httpPlatform>` prvku *web.config*, kde `processPath` atribut odkazuje na interpret Pythonu rozšíření webu a `arguments` atribut odkazuje na váš skript a všechny argumenty, které chcete poskytnout:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

`HTTP_PLATFORM_PORT`Zde uvedená proměnná prostředí obsahuje port, na kterém by měl váš místní server naslouchat připojením z místního hostitele. Tento příklad také ukazuje, jak vytvořit další proměnnou prostředí, pokud je to potřeba, v tomto případě `SERVER_PORT` .

### <a name="configure-the-fastcgi-handler"></a>Konfigurace obslužné rutiny FastCGI

FastCGI je rozhraní, které funguje na úrovni žádosti. Služba IIS přijímá příchozí připojení a přepošle každý požadavek do aplikace rozhraním WSGI spuštěné v jednom nebo několika trvalých procesech Pythonu.

Pokud ho chcete použít, nejdřív nainstalujte a nakonfigurujte balíček wfastcgi, jak je popsáno na [PyPI.org/Project/wfastcgi/](https://pypi.io/project/wfastcgi).

Dále upravte soubor *web.config* vaší aplikace tak, aby obsahoval úplné cesty *python.exe* a *wfastcgi.py* v `PythonHandler` klíči. Níže uvedený postup předpokládá, že Python je nainstalovaný v *c:\python36-32* a že je váš kód aplikace v *c:\home\site\wwwroot*. odpovídajícím způsobem upravte své cesty:

1. Upravte `PythonHandler` položku v *web.config* tak, aby cesta odpovídala umístění instalace Pythonu (podrobnosti najdete v tématu [konfigurační Reference služby IIS](https://www.iis.net/configreference) (IIS.NET)).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. V `<appSettings>` části *web.config*přidejte klíče pro `WSGI_HANDLER` , `WSGI_LOG` (volitelné) a `PYTHONPATH` :

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Tyto `<appSettings>` hodnoty jsou k dispozici pro vaši aplikaci jako proměnné prostředí:

    - Hodnota pro `PYTHONPATH` může být volně rozšířená, ale musí obsahovat kořen vaší aplikace.
    - `WSGI_HANDLER`musí odkazovat na aplikaci rozhraním WSGI, kterou lze importovat z vaší aplikace.
    - `WSGI_LOG`je volitelná, ale doporučuje se pro ladění vaší aplikace.

1. Nastavte `WSGI_HANDLER` položku v *web.config* dle potřeby pro rozhraní, které používáte:

    - **Láhev**: Ujistěte se, že máte kulaté závorky, `app.wsgi_app` jak je znázorněno níže. To je nezbytné, protože tento objekt je funkce (viz *App.py*) místo proměnné:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Baňka**: změňte `WSGI_HANDLER` hodnotu na `<project_name>.app` , kde se `<project_name>` shoduje s názvem vašeho projektu. Přesný identifikátor najdete tak, že si prohlížíte `from <project_name> import app` příkaz v *runserver.py*. Například pokud má projekt název "FlaskAzurePublishExample", položka by se zobrazila takto:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: pro *web.config* pro projekty Django jsou potřeba dvě změny. Nejprve změňte `WSGI_HANDLER` hodnotu na `django.core.wsgi.get_wsgi_application()` (objekt je v souboru *WSGI.py* ):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Za druhé přidejte následující položku pro `WSGI_HANDLER` , nahraďte `DjangoAzurePublishExample` názvem projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Jenom aplikace Django**: v souboru *Settings.py* projektu Django přidejte adresu URL vaší lokality nebo IP adresu, `ALLOWED_HOSTS` jak je znázorněno níže. nahraďte "1.2.3.4" adresou URL nebo IP adresou, samozřejmě:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Nepovedlo se přidat vaši adresu URL do pole, výsledkem je chyba **DisallowedHost na/neplatné hlavičce HTTP_HOST: ' \<site URL\> '. Je možné, že budete muset přidat ' \<site URL\> ' do ALLOWED_HOSTS.**

    Všimněte si, že pokud je pole prázdné, Django automaticky povoluje "localhost" a "127.0.0.1", ale přidání vaší produkční adresy URL tyto možnosti odebere. Z tohoto důvodu můžete chtít udržovat samostatné vývojové a produkční kopie *Settings.py*nebo použít proměnné prostředí k řízení hodnot doby běhu.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Nasazení do služby IIS nebo virtuálního počítače s Windows

Se správným souborem *web.config* v projektu můžete publikovat do počítače se službou IIS pomocí příkazu **publikovat** v místní nabídce projektu v **Průzkumník řešení**a vybrat možnost, **IIS, FTP atd.**. V tomto případě Visual Studio jednoduše zkopíruje soubory projektu na server; Zodpovídáte za všechny konfigurace na straně serveru.
