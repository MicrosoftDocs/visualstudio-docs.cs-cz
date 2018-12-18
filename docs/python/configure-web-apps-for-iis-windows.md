---
title: Konfigurace webové aplikace v Pythonu pro službu IIS
description: Postup konfigurace webové aplikace v Pythonu pomocí Internetové informační služby z virtuálního počítače Windows.
ms.date: 12/06/2018
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
ms.openlocfilehash: 8de69c64cac5c841867f5d993395e5ab380625eb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062895"
---
# <a name="configure-python-web-apps-for-iis"></a>Konfigurace webové aplikace v Pythonu pro službu IIS

Při použití Internetové informační služby (IIS) jako webový server na počítači Windows (včetně [virtuální počítače s Windows v Azure](/azure/architecture/reference-architectures/n-tier/windows-vm), aplikace v Pythonu musí obsahovat konkrétní nastavení v jejich *web.config* soubory, zda služba IIS zpracovávat správně kódu Pythonu. Přímo počítač musí mít také nainstalována spolu s všechny balíčky, které vyžaduje webové aplikace Python.

> [!Note]
> Tento článek obsahoval dříve pokyny ke konfiguraci Pythonu ve službě Azure App Service ve Windows. Rozšíření Pythonu a hostitele Windows použité v tomto scénáři jsou zastaralé a místo toho použití služby Azure App Service v Linuxu. Další informace najdete v tématu [publikování aplikace v Pythonu do služby Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Předchozí článek, ale je stále k dispozici [Správa služby App Service ve Windows s rozšířeními Python](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Nainstalovat Python ve Windows

Ke spuštění webové aplikace, nejprve nainstalovat vaše požadované verzi Pythonu přímo na hostitelském počítači Windows jak je popsáno na [interpretů Pythonu nainstalujte](installing-python-interpreters.md).

Zaznamenejte umístění `python.exe` interpret v pozdějších krocích. Pro usnadnění práce můžete přidat toto umístění do proměnné prostředí PATH.

## <a name="install-packages"></a>Instalace balíčků

Při používání vyhrazeného hostitele, můžete použít globální prostředí Pythonu ke spouštění vaší aplikace, nikoli do virtuálního prostředí. Toho můžete nainstalovat všechny požadavky vaší aplikace do globálního prostředí jednoduše spuštěním `pip install -r requirements.txt` z příkazového řádku.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Nastavení web.config tak, aby odkazoval na interpret Pythonu

Vaše aplikace *web.config* souboru nastaví na webovém serveru IIS (7 +), o jak zpracovávat požadavky Python prostřednictvím FastCGI nebo HttpPlatform a systémem Windows. Když pomocí sady Visual Studio 2017, je třeba upravit *web.config* ručně. Jak je popsáno v další části, Visual Studio 2015 umožňuje úpravy

### <a name="configure-the-httpplatform-handler"></a>Konfigurace HttpPlatform obslužné rutiny

Modul HttpPlatform předá připojení soketu přímo do samostatného procesu Pythonu. Tato předávací umožňuje spouštět jakékoli webové servery, jako jsou, ale vyžaduje spouštěcí skript, který spustí místní webový server. Zadejte skript v `<httpPlatform>` prvek *web.config*, kde `processPath` atribut body k interpretu Pythonu rozšíření webu a `arguments` atribut odkazuje na skript a argumentů Chcete poskytnout:

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

`HTTP_PLATFORM_PORT` Proměnná prostředí je vidět tady obsahuje port, který váš místní server naslouchat požadavkům na připojení z místního hostitele. Tento příklad také ukazuje, jak vytvořit další proměnné prostředí, v případě potřeby v tomto případě `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Konfigurace obslužná rutina FastCGI

FastCGI je rozhraní, které funguje na úrovni požadavků. Přijímá příchozí připojení služby IIS a předá každý požadavek s rozhraním WSGI aplikace spuštěná v jednom nebo více trvalých Python procesy.

Jeho použití, první instalaci a konfiguraci balíčku wfastcgi, jak je popsáno v [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

V dalším kroku upravit svou aplikaci *web.config* zahrnout úplné cesty k souboru *python.exe* a *wfastcgi.py* v `PythonHandler` klíč. Následující postup předpokládá, že je nainstalován Python v *c:\python36-32* a že je váš kód aplikace v *c:\home\site\wwwroot*; odpovídajícím způsobem upravit pro vaše cesty:

1. Upravit `PythonHandler` záznam v *web.config* tak, aby odpovídalo cesta umístění instalace Pythonu (naleznete v tématu [odkaz Konfigurace služby IIS](https://www.iis.net/configreference) (iis.net) najdete přesné informace).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. V rámci `<appSettings>` část *web.config*, přidejte klíče pro `WSGI_HANDLER`, `WSGI_LOG` (volitelné), a `PYTHONPATH`:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Tyto `<appSettings>` hodnoty budou dostupné pro vaši aplikaci jako proměnné prostředí:

    - Hodnota pro `PYTHONPATH` volně prodloužit, ale musí obsahovat kořenovém adresáři aplikace.
    - `WSGI_HANDLER` musí odkazovat na aplikaci s rozhraním WSGI importovatelnou z vaší aplikace.
    - `WSGI_LOG` je volitelný, ale doporučený pro ladění vaší aplikace.

1. Nastavte `WSGI_HANDLER` záznam v *web.config* podle potřeby pro architekturu používáte:

    - **Bottle**: Ujistěte se, že máte závorek za `app.wsgi_app` jak je znázorněno níže. To je nezbytné, protože tento objekt je funkce (viz *app.py*) namísto proměnné:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: Změna `WSGI_HANDLER` hodnota, která se `<project_name>.app` kde `<project_name>` odpovídá názvu vašeho projektu. Můžete najít přesně identifikátor pohledem `from <project_name> import app` příkaz v *runserver.py*. Například pokud má projekt název "FlaskAzurePublishExample", položka bude vypadat takto:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: dvě změny, které jsou potřeba k *web.config* pro projekty v Django. Nejprve změňte `WSGI_HANDLER` hodnota, která se `django.core.wsgi.get_wsgi_application()` (objekt je ve *wsgi.py* souboru):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Za druhé, přidejte následující položku níže pro `WSGI_HANDLER`a nahraďte `DjangoAzurePublishExample` s názvem vašeho projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Jenom aplikace Django**: projekt v Django *settings.py* přidejte lokality adresa URL domény nebo IP adresu, která `ALLOWED_HOSTS` jak je znázorněno níže, nahradíte '1.2.3.4' vaše adresa URL nebo IP adresa, samozřejmě:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Nepodařilo se přidat adresu URL svého výsledky do pole chyby **DisallowedHost na / neplatné záhlaví HTTP_HOST: "\<URL webu\>". Budete muset přidat "\<URL webu\>" k ALLOWED_HOSTS.**

    Pamatujte, že pokud je pole prázdné, Django, automaticky umožňuje "localhost" a "127.0.0.1", ale přidáte vaše adresa URL výroby odebere tyto možnosti. Pro kopie z tohoto důvodu můžete chtít udržovat samostatnou vývoje a provozu *settings.py*, nebo použít proměnné prostředí pro řízení běhu hodnoty.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Nasazení do služby IIS nebo virtuálního počítače Windows

Se správnými *web.config* souboru ve vašem projektu, můžete publikovat na počítači se službou IIS pomocí **publikovat** příkazu v místní nabídce projektu v **Průzkumníka řešení**a výběrem možnosti **služby IIS, FTP atd.**. V takovém případě sady Visual Studio jednoduše zkopíruje soubory projektu na serveru. Zodpovídáte za všechny konfigurace na straně serveru.
