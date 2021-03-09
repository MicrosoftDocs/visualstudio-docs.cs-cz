---
title: Konfigurace Pythonu na Azure App Service (Windows)
description: Jak nainstalovat překladač Pythonu a knihovny na Azure App Service a nakonfigurovat webové aplikace tak, aby se na tento překladač správně odkazovaly.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f7c874a5cd2742f795c6d8b04db88b98b19a556d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470011"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Jak nastavit prostředí Pythonu v Azure App Service (Windows)

> [!Important]
> Společnost Microsoft zastarala o rozšířeních Pythonu pro App Service ve Windows, jak je popsáno v tomto článku, a přihlaste se k přímému nasazení pro [App Service na Linux](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Azure App Service](https://azure.microsoft.com/services/app-service/) je nabídka typu platforma jako služba pro webové aplikace, ať už se jedná o weby, ke kterým se přistupoval prostřednictvím prohlížeče, rozhraní REST API používaných vašimi vlastními klienty nebo zpracování aktivovaného událostmi. App Service plně podporuje použití Pythonu k implementaci aplikací.

Přizpůsobitelná podpora Pythonu pro Azure App Service je k dispozici jako sada App Service *rozšíření webu* , která obsahují konkrétní verzi modulu runtime Pythonu. Následně můžete nainstalovat všechny požadované balíčky přímo do prostředí, jak je popsáno v tomto článku. Přizpůsobením prostředí v samotné App Service nemusíte spravovat balíčky v projektech webové aplikace ani nahrávat je pomocí kódu aplikace.

> [!Tip]
> I když App Service ve výchozím nastavení má Python 2,7 a Python 3,4 nainstalované v kořenových složkách na serveru, nemůžete v těchto prostředích upravovat ani instalovat balíčky, ani nemusíte záviset na jejich přítomnosti. Místo toho byste měli spoléhat na rozšíření webového serveru, které ovládáte, jak je popsáno v tomto článku.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Vyberte verzi Pythonu pomocí Azure Portal

1. Vytvořte App Service pro vaši webovou aplikaci na Azure Portal.
1. Na stránce App Service přejděte do části **vývojové nástroje** , vyberte **rozšíření** a pak vyberte **+ Přidat**.
1. Posuňte se dolů v seznamu k rozšíření obsahujícímu požadovanou verzi Pythonu:

    ![Azure Portal zobrazení rozšíření Pythonu](media/python-on-azure-extensions.png)

    > [!Tip]
    > Pokud potřebujete starší verzi Pythonu a nevidíte ji uvedenou v rozšířeních lokality, můžete ji i nadále instalovat prostřednictvím Azure Resource Manager, jak je popsáno v následující části.

1. Vyberte rozšíření, přijměte právní podmínky a pak vyberte **OK**.
1. Po dokončení instalace se na portálu zobrazí oznámení.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Vyberte verzi Pythonu pomocí Azure Resource Manager

Pokud nasazujete App Service se šablonou Azure Resource Manager, přidejte rozšíření webu jako prostředek. Konkrétně se rozšíření zobrazí jako vnořený prostředek ( `resources` objekt v rámci `resources` ) s typem `siteextensions` .

Například po přidání odkazu na `python361x64` (Python 3.6.1 x64) může šablona vypadat jako v následujícím příkladu (některé vlastnosti jsou vynechány):

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

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Nastavit web.config, aby odkazovaly na interpret Pythonu

Po instalaci rozšíření lokality (prostřednictvím portálu nebo šablony Azure Resource Manager) budete dál nasměrovat soubor *web.config* aplikace na interpret Pythonu. *web.config* soubor dává pokyn webovému serveru služby IIS (7 +) běžícímu na App Service o tom, jak by měl zpracovávat požadavky Pythonu prostřednictvím HttpPlatform (doporučeno) nebo FastCGI.

Začněte tím, že vyhledáte úplnou cestu k *python.exe* rozšíření lokality a pak vytvoříte a upravíte příslušný *web.config* soubor.

### <a name="find-the-path-to-pythonexe"></a>Najděte cestu k python.exe

Rozšíření webu Python je nainstalováno na serveru v části *d:\home* ve složce, která je vhodná pro verzi a architekturu Pythonu (kromě případu, kdy se jedná o několik starších verzí). Například Python 3.6.1 x64 je nainstalován v *d:\home\python361x64*. Pak se *d:\home\python361x64\python.exe* úplná cesta k interpretu Pythonu.

Chcete-li zobrazit konkrétní cestu v App Service, vyberte **rozšíření** na stránce App Service a pak vyberte rozšíření v seznamu.

![Seznam rozšíření na Azure App Service](media/python-on-azure-extension-list.png)

Tato akce otevře stránku s popisem rozšíření obsahující cestu:

![Podrobnosti o rozšíření Azure App Service](media/python-on-azure-extension-detail.png)

Pokud se vám nedaří zobrazit cestu k rozšíření, můžete ji najít ručně pomocí konzoly:

1. Na stránce App Service vyberte   >  **konzolu** vývojové nástroje.
1. Zadejte příkaz `ls ../home` nebo `dir ..\home` Zobrazte složky rozšíření nejvyšší úrovně, například *Python361x64*.
1. Zadejte příkaz, například `ls ../home/python361x64` nebo `dir ..\home\python361x64` , aby bylo možné ověřit, zda obsahuje *python.exe* a jiné soubory interpretu.

### <a name="configure-the-httpplatform-handler"></a>Konfigurace obslužné rutiny HttpPlatform

Modul HttpPlatform předá připojení soketů přímo k samostatnému procesu Pythonu. Tato předávací rutina umožňuje spustit libovolný webový server, který chcete, ale vyžaduje spouštěcí skript, který spouští místní webový server. Zadáte skript v `<httpPlatform>` prvku *web.config*, kde `processPath` atribut odkazuje na interpret Pythonu rozšíření webu a `arguments` atribut odkazuje na váš skript a všechny argumenty, které chcete poskytnout:

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

`HTTP_PLATFORM_PORT`Zde uvedená proměnná prostředí obsahuje port, na kterém by měl váš místní server naslouchat připojením z místního hostitele. Tento příklad také ukazuje, jak vytvořit další proměnnou prostředí, pokud je to potřeba, v tomto případě `SERVER_PORT` .

### <a name="configure-the-fastcgi-handler"></a>Konfigurace obslužné rutiny FastCGI

FastCGI je rozhraní, které funguje na úrovni žádosti. Služba IIS přijímá příchozí připojení a přepošle každý požadavek do aplikace rozhraním WSGI spuštěné v jednom nebo několika trvalých procesech Pythonu. [Balíček wfastcgi](https://pypi.io/project/wfastcgi) je předinstalovaný a nakonfigurovaný s každým rozšířením webu Pythonu, takže ho můžete snadno povolit tak, že ho zadáte do *web.config* například, jak je uvedeno níže pro webovou aplikaci založenou na rozhraní láhve. Všimněte si, že všechny cesty k *python.exe* a *wfastcgi.py* jsou umístěné v `PythonHandler` klíči:

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

`<appSettings>`Tady definované jsou k dispozici pro vaši aplikaci jako proměnné prostředí:

- Hodnota pro `PYTHONPATH` může být volně rozšířená, ale musí obsahovat kořen vaší aplikace.
- `WSGI_HANDLER` musí odkazovat na aplikaci rozhraním WSGI, kterou lze importovat z vaší aplikace.
- `WSGI_LOG` je volitelná, ale doporučuje se pro ladění vaší aplikace.

Další podrobnosti o *web.config* obsahu pro láhev, baňce a webové aplikace v Django najdete v tématu [publikování do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) .

## <a name="install-packages"></a>Nainstalovat balíčky

Překladač Pythonu nainstalovaný prostřednictvím rozšíření lokality je jenom jedna část prostředí Pythonu. V tomto prostředí pravděpodobně budete muset nainstalovat i jiné balíčky.

Chcete-li nainstalovat balíčky přímo v prostředí serveru, použijte jednu z následujících metod:

| Metody | Využití |
| --- | --- |
| [Azure App Service konzolu Kudu](#azure-app-service-kudu-console) | Nainstaluje balíčky interaktivně. Balíčky musí být čistě Python nebo musí zveřejňovat kolaci. |
| [Kudu REST API](#kudu-rest-api) | Dá se použít k automatizaci instalace balíčku.  Balíčky musí být čistě Python nebo musí zveřejňovat kolaci. |
| Sada prostředků s aplikací | Nainstalujte balíčky přímo do projektu a pak je nasaďte do App Service, jako kdyby byly součástí vaší aplikace. V závislosti na tom, kolik závislostí máte a jak často je aktualizujete, může být tato metoda nejjednodušší způsob, jak získat funkční nasazení. Doporučujeme, aby knihovny odpovídaly verzi Pythonu na serveru. v opačném případě uvidíte po nasazení zakrýt chyby. Vzhledem k tomu, že verze Pythonu v rozšířeních App Service jsou přesně stejné jako verze vydané na python.org, můžete snadno získat kompatibilní verzi pro místní vývoj. |
| Virtuální prostředí | Nepodporováno Místo toho použijte sdružování a nastavte `PYTHONPATH` proměnnou prostředí tak, aby odkazovala na umístění balíčků. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service konzolu Kudu

[Konzola Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) poskytuje přímý přístup k serveru App Service a jeho systému souborů prostřednictvím příkazového řádku se zvýšeným oprávněním. Jedná se o hodnotný nástroj pro ladění a umožňuje operace CLI, jako je instalace balíčků.

1. Otevřete Kudu ze stránky App Service na Azure Portal tak, že vyberete **vývojové nástroje**  >  **Pokročilé nástroje** a pak vyberete **Přejít**. Tato akce přejde na adresu URL, která je stejná jako základní adresa URL App Service, s výjimkou `.scm` vloženého. Například pokud je vaše základní adresa URL, `https://vspython-test.azurewebsites.net/` pak Kudu je zapnuto `https://vspython-test.scm.azurewebsites.net/` (kterou můžete založit do záložky):

    ![Konzola Kudu pro Azure App Service](media/python-on-azure-console01.png)

1. Vyberte **ladit konzolu**  >  **cmd** a otevřete tak konzolu, ve které můžete přejít na instalaci Pythonu a podívat se, jaké knihovny už existují.

1. Instalace jednoho balíčku:

    a. Přejděte do složky instalace Pythonu, do které chcete balíček nainstalovat, například *d:\home\python361x64*.

    b. Použijte `python.exe -m pip install <package_name>` k instalaci balíčku.

    ![Příklad instalace láhve prostřednictvím konzoly Kudu pro Azure App Service](media/python-on-azure-console02.png)

1. Pokud jste nasadili *requirements.txt* pro vaši aplikaci již na server, nainstalujte všechny tyto požadavky následujícím způsobem:

    a. Přejděte do složky instalace Pythonu, do které chcete balíček nainstalovat, například *d:\home\python361x64*.

    b. Spusťte příkaz `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Doporučuje se použít *requirements.txt* , protože je snadné reprodukování přesné sady balíčků místně i na serveru. Jenom nezapomeňte navštívit konzolu po nasazení změn *requirements.txt* a znovu spustit příkaz.

> [!Note]
> V App Service není žádný kompilátor jazyka C, takže je nutné nainstalovat kolečko pro všechny balíčky s nativními rozšiřujícími moduly. Spousta oblíbených balíčků nabízí vlastní kolace. Pro balíčky, které nepoužívají `pip wheel <package_name>` na místním počítači pro vývoj a pak nahrajte kolo na svůj web. Příklad najdete v tématu [Správa požadovaných balíčků pomocí requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu REST API

Namísto použití konzoly Kudu prostřednictvím Azure Portal můžete vzdáleně spouštět příkazy prostřednictvím Kudu REST API publikováním příkazu do `https://yoursite.scm.azurewebsites.net/api/command` . Chcete-li například nainstalovat `bottle` balíček, následující kód JSON vystavte `/api/command` :

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Informace o příkazech a ověřování najdete v [dokumentaci k Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Přihlašovací údaje můžete zobrazit také pomocí `az webapp deployment list-publishing-profiles` příkazu přes rozhraní příkazového řádku Azure (viz [AZ WebApp Deployment](/cli/azure/webapp/deployment?view=azure-cli-latest&preserve-view=true#az-webapp-deployment-list-publishing-profiles)). Pomocná knihovna pro příkazy posting Kudu je k dispozici na [GitHubu](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
