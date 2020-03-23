---
title: Konfigurace Pythonu ve službě Azure App Service (Windows)
description: Jak nainstalovat překladač Pythonu a knihovny ve službě Azure App Service a konfigurace webových aplikací tak, aby správně odkazovaly na tento interpret.
ms.date: 01/07/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 7ffe0de939eba8af38c132fc3de5c96a9499e3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535959"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Jak nastavit prostředí Pythonu ve službě Azure App Service (Windows)

> [!Important]
> Společnost Microsoft zastarala rozšíření Pythonu pro službu App Service v systému Windows, jak je popsáno v tomto článku ve prospěch přímého nasazení do [služby App Service v systému Linux](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Azure App Service](https://azure.microsoft.com/services/app-service/) je nabídka platformy jako služby pro webové aplikace, ať už se jedná o weby přístupné prostřednictvím prohlížeče, REST API používané vlastními klienty nebo zpracování spouštěné událostmi. App Service plně podporuje používání Pythonu k implementaci aplikací.

Přizpůsobitelná podpora Pythonu pro Službu aplikací Azure je poskytována jako sada *rozšíření webu služby* App Service, která obsahují konkrétní verzi modulu runtime pythonu. Potom můžete nainstalovat všechny požadované balíčky přímo do tohoto prostředí, jak je popsáno v tomto článku. Přizpůsobením prostředí v samotné službě App Service nemusíte udržovat balíčky v projektech webových aplikací ani je nahrávat s kódem aplikace.

> [!Tip]
> Přestože služba App Service má ve výchozím nastavení Python 2.7 a Python 3.4 nainstalovaný v kořenových složkách na serveru, nelze přizpůsobit nebo nainstalovat balíčky v těchto prostředích, ani byste neměli záviset na jejich přítomnosti. Místo toho byste se měli spoléhat na rozšíření webu, které řídíte, jak je popsáno v tomto článku.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Výběr verze Pythonu na webu Azure Portal

1. Vytvořte službu aplikace pro webovou aplikaci na webu Azure Portal.
1. Na stránce App Service přejděte do části **Nástroje pro vývoj,** vyberte **Rozšíření**a pak vyberte **+ Přidat**.
1. Přejděte v seznamu dolů k rozšíření, které obsahuje požadovanou verzi Pythonu:

    ![Portál Azure zobrazující rozšíření Pythonu](media/python-on-azure-extensions.png)

    > [!Tip]
    > Pokud potřebujete starší verzi Pythonu a nevidíte ji uvedenou v rozšíření webu, můžete ji nainstalovat prostřednictvím Správce prostředků Azure, jak je popsáno v další části.

1. Vyberte rozšíření, přijměte zákonné podmínky a pak vyberte **OK**.
1. Po dokončení instalace se na portálu zobrazí oznámení.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Výběr verze Pythonu prostřednictvím Správce prostředků Azure

Pokud nasazujete službu App Service se šablonou Azure Resource Manager, přidejte rozšíření webu jako prostředek. Konkrétně rozšíření se zobrazí jako `resources` vnořený `resources`prostředek (objekt pod ) s typem `siteextensions` a názvem z [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Například po přidání odkazu `python361x64` na (Python 3.6.1 x64) může vaše šablona vypadat takto (některé vlastnosti jsou vynechány):

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

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Nastavení souboru web.config tak, aby přecvačiukazoval na interpret Pythonu

Po instalaci rozšíření webu (prostřednictvím portálu nebo šablony Azure Resource Manager) dále přejdete soubor *web.config* vaší aplikace na interpret a překladač Pythonu. Soubor *web.config* instruuje webový server Služby IIS (7+) spuštěný ve službě App Service o tom, jak by měl zpracovávat požadavky Pythonu prostřednictvím httpplatformy (doporučeno) nebo fastcgi.

Začněte vyhledáním úplné cesty k *souboru python.exe*rozšíření webu a poté vytvořte a upravte příslušný soubor *web.config.*

### <a name="find-the-path-to-pythonexe"></a>Najít cestu k python.exe

Rozšíření webu Pythonu je nainstalováno na serveru pod *d:\home* ve složce odpovídající verzi a architektuře Pythonu (s výjimkou několika starších verzí). Například Python 3.6.1 x64 je nainstalován v *d:\home\python361x64*. Úplná cesta k interpretu Pythonu je potom *d:\home\python361x64\python.exe*.

Pokud chcete zobrazit konkrétní cestu ve službě App Service, vyberte **rozšíření** na stránce Služba aplikace a vyberte rozšíření v seznamu.

![Seznam rozšíření ve službě Azure App Service](media/python-on-azure-extension-list.png)

Tato akce otevře stránku s popisem rozšíření obsahující cestu:

![Podrobnosti o rozšíření ve službě Azure App Service](media/python-on-azure-extension-detail.png)

Pokud máte potíže se zobrazením cesty k rozšíření, můžete ji najít ručně pomocí konzoly:

1. Na stránce Služby aplikací vyberte**konzolu** **nástrojů pro vývoj** > .
1. Zadejte `ls ../home` příkaz `dir ..\home` nebo zhlédnou složky rozšíření nejvyšší úrovně, například *Python361x64*.
1. Zadejte příkaz `ls ../home/python361x64` `dir ..\home\python361x64` jako to se mi líbí nebo ověřte, zda obsahuje *python.exe* a další interpretní soubory.

### <a name="configure-the-httpplatform-handler"></a>Konfigurace obslužné rutiny httpplatformy

Modul HttpPlatform předává připojení soketu přímo samostatnému procesu Pythonu. Tento průchod umožňuje spustit libovolný webový server, který se vám líbí, ale vyžaduje spouštěcí skript, který spouští místní webový server. Skript zadáte v `<httpPlatform>` prvku *web.config*, `processPath` kde atribut odkazuje na překladbu Pythonu rozšíření webu a `arguments` atribut odkazuje na váš skript a všechny argumenty, které chcete poskytnout:

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

Zde `HTTP_PLATFORM_PORT` zobrazená proměnná prostředí obsahuje port, na který by měl místní server naslouchat pro připojení z localhost. Tento příklad také ukazuje, jak vytvořit jinou proměnnou prostředí, pokud je to žádoucí, v tomto případě `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Konfigurace obslužné rutiny FastCGI

FastCGI je rozhraní, které funguje na úrovni požadavku. IIS přijímá příchozí připojení a předává každý požadavek do aplikace WSGI spuštěné v jednom nebo více trvalých procesech Pythonu. [Balíček wfastcgi](https://pypi.io/project/wfastcgi) je předinstalovaný a nakonfigurovaný s každým rozšířením webu Pythonu, takže jej můžete snadno povolit zahrnutím kódu do *web.config,* jako je uvedeno níže pro webovou aplikaci založenou na rozhraní Bottle Framework. Všimněte si, že úplné cesty k *python.exe* a *wfastcgi.py* jsou umístěny v klíči: `PythonHandler`

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

Zde `<appSettings>` definované jsou k dispozici pro vaši aplikaci jako proměnné prostředí:

- Hodnota pro `PYTHONPATH` může být volně rozšířena, ale musí obsahovat kořen aplikace.
- `WSGI_HANDLER`musí ukazovat na aplikaci WSGI, která se z vaší aplikace může importovat.
- `WSGI_LOG`je volitelná, ale doporučená pro ladění aplikace.

Další podrobnosti o obsahu *web.config* pro webové aplikace Bottle, Flask a Django najdete v tématu [Publish to Azure.](publishing-python-web-applications-to-azure-from-visual-studio.md)

## <a name="install-packages"></a>Instalace balíčků

Překladač Pythonu nainstalovaný prostřednictvím rozšíření webu je pouze jeden kus vašeho prostředí Pythonu. Pravděpodobně budete muset nainstalovat různé balíčky v tomto prostředí také.

Chcete-li nainstalovat balíčky přímo v prostředí serveru, použijte jednu z následujících metod:

| Metody | Využití |
| --- | --- |
| [Konzola Kudu služby Azure App Service](#azure-app-service-kudu-console) | Nainstaluje balíčky interaktivně. Balíčky musí být čistě Python nebo musí publikovat kola. |
| [Kudu REST API](#kudu-rest-api) | Lze použít k automatizaci instalace balíčku.  Balíčky musí být čistě Python nebo musí publikovat kola. |
| Balíček s aplikací | Nainstalujte balíčky přímo do projektu a pak je nasaďte do služby App Service, jako by byly součástí vaší aplikace. V závislosti na tom, kolik závislostí máte a jak často je aktualizujete, může být tato metoda nejjednodušším způsobem, jak začít pracovat s pracovním nasazením. Upozorňujeme, že knihovny musí odpovídat verzi Pythonu na serveru, jinak se po nasazení zobrazí nejasné chyby. To znamená, že vzhledem k tomu, že verze Pythonu v rozšířeníwebu Služby aplikací jsou přesně stejné jako verze vydané v python.org, můžete snadno získat kompatibilní verzi pro místní vývoj. |
| Virtuální prostředí | Není podporováno. Místo toho použijte sdružování a nastavte proměnnou `PYTHONPATH` prostředí tak, aby ukazovala na umístění balíčků. |

### <a name="azure-app-service-kudu-console"></a>Konzola Kudu služby Azure App Service

[Konzole Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) poskytuje přímý, zvýšený přístup k serveru App Service a jeho souborovému systému. Jedná se o cenný ladicí nástroj a umožňuje operace v rámci systému řízení chování, jako je například instalace balíčků.

1. Otevřete Kudu ze stránky Služby aplikací na webu Azure Portal tak, že vyberete **pokročilé nástroje pro** > vývoj**a**pak vyberete **Přejít**. Tato akce přejde na adresu URL, která je stejná `.scm` jako vaše základní adresa URL služby App Service s výjimkou vložené. Pokud je `https://vspython-test.azurewebsites.net/` například vaše základní adresa URL, je na `https://vspython-test.scm.azurewebsites.net/` ní Kudu (kterou si můžete připletit do záložek):

    ![Konzole Kudu pro službu Azure App Service](media/python-on-azure-console01.png)

1. Vyberte **Ladicí konzola** > **CMD** otevřete konzolu, ve které můžete přejít do instalace Pythonu a zjistit, jaké knihovny již existují.

1. Instalace jednoho balíčku:

    a. Přejděte do složky instalace Pythonu, do které chcete balíček nainstalovat, například *d:\home\python361x64*.

    b. Slouží `python.exe -m pip install <package_name>` k instalaci balíčku.

    ![Příklad instalace láhve prostřednictvím konzole Kudu pro službu Azure App Service](media/python-on-azure-console02.png)

1. Pokud jste již pro aplikaci nasadili *soubor requirements.txt* pro aplikaci na server, nainstalujte všechny tyto požadavky takto:

    a. Přejděte do složky instalace Pythonu, do které chcete balíček nainstalovat, například *d:\home\python361x64*.

    b. Spusťte příkaz `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Použití *souboru requirements.txt* se doporučuje, protože je snadné reprodukovat přesnou sadu balíčků jak místně, tak na serveru. Nezapomeňte navštívit konzolu po nasazení všech změn *na requirements.txt* a znovu spustit příkaz.

> [!Note]
> Ve službě App Service není žádný kompilátor Jazyka C, takže je třeba nainstalovat kolečko pro všechny balíčky s nativními rozšiřujícími moduly. Mnoho populárních balíčků poskytuje vlastní kola. U balíčků, které ne, použijte `pip wheel <package_name>` v místním vývojovém počítači a nahrajte kolo na svůj web. Příklad naleznete v tématu [Správa požadovaných balíčků pomocí souboru requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu REST API

Místo použití konzoly Kudu prostřednictvím portálu Azure můžete spouštět příkazy vzdáleně prostřednictvím rozhraní API Kudu REST odesláním příkazu do `https://yoursite.scm.azurewebsites.net/api/command`. Chcete-li například `bottle` nainstalovat balíček, zaúčtujte následující příspěvek na následující aplikaci JSON do `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Informace o příkazech a ověřování naleznete v [dokumentaci kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Můžete také zobrazit přihlašovací `az webapp deployment list-publishing-profiles` údaje pomocí příkazu prostřednictvím příkazu Azure CLI (viz [nasazení az webapp](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Pomocná knihovna pro odesílání příkazů Kudu je k dispozici na [GitHubu](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
