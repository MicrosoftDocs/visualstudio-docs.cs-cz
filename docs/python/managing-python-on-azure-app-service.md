---
title: Konfigurace Pythonu ve službě Azure App Service (Windows)
description: Postup instalace překladače a knihoven Pythonu ve službě Azure App Service a konfiguraci webové aplikace správně odkazovat na tomto interpretu.
ms.date: 10/18/2018
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
ms.openlocfilehash: e21be06c26ec6a15b46ef72c0fe33a35b314c989
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051290"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Jak nastavit prostředí Pythonu ve službě Azure App Service (Windows)

> [!Important]
> Microsoft se nepoužívá rozšíření Pythonu pro službu App Service na Windows, jak je popsáno v tomto článku ve prospěch přímé nasazení do [App Service v Linuxu](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Azure App Service](https://azure.microsoft.com/services/app-service/) je jako nabídka platforma jako služba pro webové aplikace, ať už jsou weby přístupných prostřednictvím prohlížeče, rozhraní REST API, používat vlastní klienty nebo událost aktivuje zpracování. App Service podporuje použití Pythonu k implementaci aplikace.

Přizpůsobitelné podpory Pythonu pro službu Azure App Service se poskytuje jako sady služby App Service *rozšířením webu* , že každý obsahuje konkrétní verzi modulu runtime Pythonu. Poté můžete nainstalovat všechny požadované balíčky, které přímo do daného prostředí, jak je popsáno v tomto článku. Přizpůsobením prostředí ve službě App Service, samotného, není nutné udržovat balíčky v projektech webových aplikací nebo nahrávat společně s kódem aplikace.

> [!Tip]
> Ačkoli App Service ve výchozím nastavení se Python 2.7 a Python 3.4 nainstalovat do kořenové složky na serveru, nejde upravit nebo nainstalovat balíčky v těchto prostředích, ani by měl záviset na jejich přítomnost. Se místo toho spoléhají na rozšíření webu, který určujete vy, jak je popsáno v tomto článku.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Zvolte verzi Pythonu na webu Azure portal

1. Vytvoření služby App Service pro vaši webovou aplikaci na webu Azure portal.
1. Na stránce služby App Service, přejděte **nástroje pro vývoj** vyberte **rozšíření**a pak vyberte **+ přidat**.
1. Přejděte dolů v seznamu, který obsahuje verzi jazyka Python, které chcete, aby rozšíření:

    ![Rozšíření Azure Portalu zobrazující Pythonu](media/python-on-azure-extensions.png)

    > [!Tip]
    > Pokud potřebujete starší verze jazyka Python a nezobrazuje uvedené v rozšíření webu, můžete nainstalovat ho prostřednictvím Azure Resource Manageru jak je popsáno v další části.

1. Vyberte rozšíření, přijměte právní podmínky a pak vyberte **OK**.
1. Oznámení se zobrazí na portálu po dokončení instalace.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Zvolte verzi Pythonu prostřednictvím Azure Resource Manageru

Pokud provádíte nasazení služby App Service pomocí šablony Azure Resource Manageru, přidáte rozšíření webu jako prostředek. Konkrétně se rozšíření zobrazí jako vnořený prostředek ( `resources` objekt v rámci `resources`) s typem `siteextensions` a název z [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Například po přidání odkazu na `python361x64` (Python 3.6.1 x 64), vaše šablona může vypadat třeba takto (vynechány některé vlastnosti):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Nastavení web.config tak, aby odkazoval na interpret Pythonu

Po instalaci rozšíření webu (pomocí portálu nebo šablony Azure Resource Manageru), dále odkazovat vaše aplikace *web.config* soubor pro interpret Pythonu. *Web.config* souboru nastaví na webovém serveru IIS (7 +), o jak zpracovávat požadavky Python prostřednictvím FastCGI nebo HttpPlatform běžící na App Service.

Začněte tím, že hledání úplnou cestu k rozšíření webu *python.exe*, vytvořte a upravte příslušné *web.config* souboru.

### <a name="find-the-path-to-pythonexe"></a>Najít cestu ke python.exe

Rozšíření webu Python je nainstalována na serveru v části *d:\home* ve složce příslušná verze Pythonu a architektura (s výjimkou několika starší verze). Například Python 3.6.1 x64 nainstalovaný v *d:\home\python361x64*. Úplná cesta k interpretu Pythonu je pak *d:\home\python361x64\python.exe*.

Pokud chcete zobrazit konkrétní cesty ve službě App Service, vyberte **rozšíření** na stránce služby App Service, pak vyberte rozšíření v seznamu.

![Seznam rozšíření ve službě Azure App Service](media/python-on-azure-extension-list.png)

Tato akce otevře stránku rozšíření popis obsahující cestu:

![Podrobnosti o rozšíření ve službě Azure App Service](media/python-on-azure-extension-detail.png)

Pokud máte potíže s zobrazuje cestu k rozšíření, najdete ho ručně pomocí konzoly:

1. Na stránce služby App Service, vyberte **nástroje pro vývoj** > **konzoly**.
1. Zadejte příkaz `ls ../home` nebo `dir ..\home` zobrazíte složky nejvyšší úrovně rozšíření *Python361x64*.
1. Zadejte příkaz podobný `ls ../home/python361x64` nebo `dir ..\home\python361x64` k ověření, že obsahuje *python.exe* a další soubory překladač.

### <a name="configure-the-fastcgi-handler"></a>Konfigurace obslužná rutina FastCGI

FastCGI je rozhraní, které funguje na úrovni požadavků. Přijímá příchozí připojení služby IIS a předá každý požadavek s rozhraním WSGI aplikace spuštěná v jednom nebo více trvalých Python procesy. [Wfastcgi balíčku](https://pypi.io/project/wfastcgi) předem nainstalovaná a nakonfigurovaná s každou rozšíření webu Pythonu, takže je můžete snadno povolit kódu v *web.config* , jako jsou zobrazené níže pro webové aplikace na základě Rozhraní Bottle. Všimněte si, že úplné cesty k *python.exe* a *wfastcgi.py* jsou umístěny v `PythonHandler` klíč:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` Definované, tady jsou k dispozici pro vaši aplikaci jako proměnné prostředí:

- Hodnota pro `PYTHONPATH` volně prodloužit, ale musí obsahovat kořenovém adresáři aplikace.
- `WSGI_HANDLER` musí odkazovat na aplikaci s rozhraním WSGI importovatelnou z vaší aplikace.
- `WSGI_LOG` je volitelný, ale doporučený pro ladění vaší aplikace. 

V tématu [publikovat do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) najdete další podrobnosti o *web.config* obsah pro Bottle, Flask a Django webové aplikace.

### <a name="configure-the-httpplatform-handler"></a>Konfigurace HttpPlatform obslužné rutiny

Modul HttpPlatform předá připojení soketu přímo do samostatného procesu Pythonu. Tato předávací umožňuje spouštět jakékoli webové servery, jako jsou, ale vyžaduje spouštěcí skript, který spustí místní webový server. Zadejte skript v `<httpPlatform>` prvek *web.config*, kde `processPath` atribut body k interpretu Pythonu rozšíření webu a `arguments` atribut odkazuje na skript a argumentů Chcete poskytnout:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
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

## <a name="install-packages"></a>Instalace balíčků

Interpret Pythonu nainstalované prostřednictvím rozšíření webu je pouze jedna část prostředí Pythonu. Budete pravděpodobně muset nainstalovat různých balíčcích v tomto prostředí také.

K instalaci balíčků přímo v prostředí serveru, použijte jednu z následujících metod:

| Metody | Použití |
| --- | --- |
| [Azure App Service Kudu konzoly](#azure-app-service-kudu-console) | Nainstaluje balíčky interaktivně. Balíčky musí být čistě Python nebo musíte publikovat kola. |
| [Rozhraní REST API služby kudu](#kudu-rest-api) | Můžete použít k automatizaci instalace balíčku.  Balíčky musí být čistě Python nebo musíte publikovat kola. |
| Vytvoření balíčku aplikace | Instalace balíčků přímo do vašeho projektu a pak je nasadit do služby App Service, jako by byly součástí vaší aplikace. V závislosti na tom, kolik závislostí máte a jak často je aktualizovat, tato metoda může být nejjednodušší způsob, jak získat pracovní nasazení. Informováni, že knihovny musí odpovídat verzi jazyka Python na serveru, v opačném případě se zobrazí chyby skrytého po nasazení. Ale nutné dodat, protože verze Pythonu ve službě App Service rozšíření webu jsou stejné jako všeobecně dostupné na webu python.org verzí, můžete snadno získat kompatibilní verze pro místní vývoj. |
| Virtuální prostředí | Není podporováno. Místo toho použijte sdružování a nastavte `PYTHONPATH` proměnnou prostředí, aby odkazovalo na umístění balíčky. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service Kudu konzoly

[Konzola Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) umožňuje přístup příkazového řádku s přímým přístupem, se zvýšenými oprávněními na serveru služby App Service a její systému souborů. Tím se oba cenné ladicí nástroj a umožňuje operace rozhraní příkazového řádku, například při instalaci balíčků.

1. Na stránce služby App Service na portálu Azure portal výběrem otevřete Kudu **nástroje pro vývoj** > **Rozšířené nástroje**, pak vyberete **Přejít**. Tato akce přejde na adresu URL, která je stejná jako vaše základní adresa URL služby aplikace s výjimkou s `.scm` vložen. Například, pokud je základní adresa URL `https://vspython-test.azurewebsites.net/` Kudu je na `https://vspython-test.scm.azurewebsites.net/` (což můžete stránku):

    ![Konzola Kudu pro službu Azure App Service](media/python-on-azure-console01.png)

1. Vyberte **konzolou pro ladění** > **CMD** otevřete konzoly, ve kterém můžete přejít do instalace Pythonu a zjistit, co knihovny jsou již existuje.

1. Chcete-li nainstalovat jeden balíček:

    a. Přejděte do složky instalace Pythonu, ve které chcete balíček nainstalovat, například *d:\home\python361x64*.

    b. Použití `python.exe -m pip install <package_name>` k instalaci balíčku.

    ![Příklad instalace bottle prostřednictvím konzoly Kudu pro službu Azure App Service](media/python-on-azure-console02.png)

1. Pokud jste nasadili *souboru requirements.txt* pro vaši aplikaci na server již, nainstalujte všechny tyto požadavky následujícím způsobem:

    a. Přejděte do složky instalace Pythonu, ve které chcete balíček nainstalovat, například *d:\home\python361x64*.

    b. Spusťte příkaz `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Pomocí *souboru requirements.txt* se doporučuje, protože je snadné ji reprodukovat přesné balíčku nastavte lokálně a na serveru. Jenom nezapomeňte pro návštěvu konzole po nasazení jakékoli změny *souboru requirements.txt* a spusťte příkaz znovu.

> [!Note]
> Neexistuje žádný kompilátor jazyka C ve službě App Service, takže je potřeba nainstalovat kolečko pro všechny balíčky s nativní rozšiřující moduly. Mnoho oblíbených balíčků poskytnout jejich vlastní kola. Pro balíčky, které ji nemají, použijte `pip wheel <package_name>` na místním počítači pro vývoj a nahrajete kolečka na váš web. Příklad najdete v tématu [spravovat vyžadované balíčky pomocí souboru requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Rozhraní REST API služby kudu

Namísto použití konzoly Kudu na webu Azure portal, můžete spouštět příkazy vzdáleně přes rozhraní REST API Kudu tím, že příkaz, který publikuje `https://yoursite.scm.azurewebsites.net/api/command`. Například, chcete-li nainstalovat `bottle` balíček, publikovat následující JSON na `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Informace o příkazech a ověřování najdete v tématu [Kudu dokumentaci](https://github.com/projectkudu/kudu/wiki/REST-API).

Můžete také zjistit pomocí přihlašovacích údajů `az webapp deployment list-publishing-profiles` příkaz přes rozhraní příkazového řádku Azure (viz [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Je k dispozici na pomocné knihovny pro odesílání příkazů Kudu [Githubu](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
