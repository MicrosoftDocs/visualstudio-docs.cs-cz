---
title: Konfigurace webových aplikací Pythonu pro službu IIS
description: Jak nakonfigurovat webové aplikace Pythonu tak, aby běžely pomocí Internetové informační služby z virtuálního počítače s Windows.
ms.date: 12/06/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 551cff18849f0e8ad9fcd6f2c1e08561291b177f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957369"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurace webových aplikací Pythonu pro službu IIS

Při použití Internetové informační služby (IIS) jako webového serveru v počítači se systémem Windows (včetně [virtuálních počítačů s Windows](/azure/architecture/reference-architectures/n-tier/windows-vm)v Azure musí aplikace Pythonu obsahovat konkrétní nastavení ve svých souborech *web.config,* aby služba IIS mohla správně zpracovat kód Pythonu. Samotný počítač musí mít také nainstalovaný Python spolu se všemi balíčky, které webová aplikace vyžaduje.

> [!Note]
> Tento článek dříve obsahoval pokyny pro konfiguraci Pythonu ve službě Azure App Service ve Windows. Rozšíření Pythonu a hostitelé Windows, kteří se používají v tomto scénáři, jsou zastaralé ve prospěch služby Azure App Service na Linuxu. Další informace najdete [v tématu publikování aplikací Pythonu do služby Azure App Service (Linux).](publishing-python-web-applications-to-azure-from-visual-studio.md) Předchozí článek je však stále k dispozici na [správě služby App Service v systému Windows s rozšířeními Pythonu](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Instalace Pythonu ve Windows

Chcete-li spustit webovou aplikaci, nejprve nainstalujte požadovanou verzi Pythonu přímo na hostitelský počítač windows, jak je popsáno v [interpretech Install Python](installing-python-interpreters.md).

Zaznamenejte `python.exe` umístění interpretu pro pozdější kroky. Pro větší pohodlí můžete přidat toto umístění do proměnné prostředí PATH.

## <a name="install-packages"></a>Instalace balíčků

Při použití vyhrazeného hostitele můžete ke spuštění aplikace místo virtuálního prostředí použít globální prostředí Pythonu. V souladu s tím můžete nainstalovat všechny požadavky aplikace do `pip install -r requirements.txt` globálního prostředí jednoduše spuštěním na příkazovém řádku.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Nastavení souboru web.config tak, aby přecvačiukazoval na interpret Pythonu

Soubor *web.config* vaší aplikace instruuje webový server Služby IIS (7+) spuštěný v systému Windows o tom, jak by měl zpracovávat požadavky Pythonu prostřednictvím httpplatformy (doporučeno) nebo fastcgi. Visual Studio verze 2015 a starší provádět tyto změny automaticky. Při použití sady Visual Studio 2017 a novější je nutné ručně upravit *web.config.*

### <a name="configure-the-httpplatform-handler"></a>Konfigurace obslužné rutiny httpplatformy

Modul HttpPlatform předává připojení soketu přímo samostatnému procesu Pythonu. Tento průchod umožňuje spustit libovolný webový server, který se vám líbí, ale vyžaduje spouštěcí skript, který spouští místní webový server. Skript zadáte v `<httpPlatform>` prvku *web.config*, `processPath` kde atribut odkazuje na překladbu Pythonu rozšíření webu a `arguments` atribut odkazuje na váš skript a všechny argumenty, které chcete poskytnout:

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

Zde `HTTP_PLATFORM_PORT` zobrazená proměnná prostředí obsahuje port, na který by měl místní server naslouchat pro připojení z localhost. Tento příklad také ukazuje, jak vytvořit jinou proměnnou prostředí, pokud je to žádoucí, v tomto případě `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Konfigurace obslužné rutiny FastCGI

FastCGI je rozhraní, které funguje na úrovni požadavku. IIS přijímá příchozí připojení a předává každý požadavek do aplikace WSGI spuštěné v jednom nebo více trvalých procesech Pythonu.

Chcete-li jej použít, nejprve nainstalujte a nakonfigurujte balíček wfastcgi, jak je popsáno na [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

Dále upravte soubor *web.config* aplikace tak, aby zahrnoval úplné cesty *wfastcgi.py* k `PythonHandler` *python.exe* a wfastcgi.py v klíči. Následující postup předpokládá, že Python je nainstalovaný v *c:\python36-32* a že kód aplikace je v *c:\home\site\wwwroot*; upravit pro vaše cesty odpovídajícím způsobem:

1. Upravte `PythonHandler` položku v *web.config* tak, aby cesta odpovídala umístění instalace Pythonu (přesné podrobnosti naleznete v [tématu Odkaz na konfiguraci služby IIS](https://www.iis.net/configreference) (iis.net).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. V `<appSettings>` části *web.config*přidejte `WSGI_HANDLER`klíče `WSGI_LOG` pro , `PYTHONPATH`(volitelné) a :

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Tyto `<appSettings>` hodnoty jsou k dispozici pro vaši aplikaci jako proměnné prostředí:

    - Hodnota pro `PYTHONPATH` může být volně rozšířena, ale musí obsahovat kořen aplikace.
    - `WSGI_HANDLER`musí ukazovat na aplikaci WSGI, která se z vaší aplikace může importovat.
    - `WSGI_LOG`je volitelná, ale doporučená pro ladění aplikace.

1. Nastavte `WSGI_HANDLER` položku v *web.config* podle potřeby pro rámec, který používáte:

    - **Láhev**: ujistěte se, že `app.wsgi_app` máte závorky po, jak je uvedeno níže. To je nezbytné, protože tento objekt je funkce (viz *app.py)* spíše než proměnná:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Baňka** `WSGI_HANDLER` : `<project_name>.app` Změňte hodnotu na místo, kde `<project_name>` se shoduje s názvem projektu. Přesný identifikátor najdete na příkazu `from <project_name> import app` v *runserver.py*. Například pokud projekt s názvem "FlaskAzurePublishExample", položka se zobrazí takto:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: Pro projekty *Django* jsou zapotřebí dvě změny. Nejprve změňte `WSGI_HANDLER` `django.core.wsgi.get_wsgi_application()` hodnotu na (objekt je v *souboru wsgi.py):*

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Za druhé, přidejte následující `WSGI_HANDLER`položku `DjangoAzurePublishExample` pod položku pro , která nahradí název projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Pouze aplikace Django**: V *souboru settings.py* projektu Django přidejte `ALLOWED_HOSTS` doménu URL webu nebo IP adresu, jak je uvedeno níže, a nahradí "1.2.3.4" vaší adresou URL nebo IP adresou, samozřejmě:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Pokud nepřidáte adresu URL do pole, dojde k chybě **DisallowedHost at / Invalid HTTP_HOST header: '\<url\>webu '. K ALLOWED_HOSTS může\<být\>nutné přidat adresu URL webu.**

    Všimněte si, že když je pole prázdné, Django automaticky povolí 'localhost' a '127.0.0.1', ale přidání mandatní adresy URL služby odebere tyto možnosti. Z tohoto důvodu můžete chtít udržovat samostatné vývojové a výrobní kopie *settings.py*nebo použít proměnné prostředí k řízení hodnot doby běhu.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Nasazení do služby IIS nebo virtuálního virtuálního mísy windows

Se správným souborem *web.config* v projektu můžete publikovat do počítače se spuštěnou službou IIS pomocí příkazu **Publikovat** v kontextové nabídce projektu v **Průzkumníku řešení**a výběrem možnosti **IIS, FTP atd.** V tomto případě Visual Studio jednoduše zkopíruje soubory projektu na server; jste zodpovědní za veškerou konfiguraci na straně serveru.
