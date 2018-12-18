---
title: Publikování aplikace v Pythonu do Azure App Service ve Windows
description: Jak publikovat webovou aplikaci Python přímo do služby Azure App Service na Windows ze sady Visual Studio, včetně nutný obsah pro soubor web.config.
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
ms.openlocfilehash: 083deb7b836bfae0b0c1352430ffb6ed4080c3dc
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248202"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publikování do služby Azure App Service ve Windows

> [!Note]
> Tento obsah a funkce popsané jsou zastaralé, ale i nadále fungovat. Jsou ukončena. doporučujeme migrovat na vývojáře v Pythonu [App Service v Linuxu](publishing-python-web-applications-to-azure-from-visual-studio.md) tam, kde je to možné.

Visual Studio poskytuje možnost publikovat webovou aplikaci Python přímo do Azure App Service na Windows. Publikování do služby Azure App Service na Windows znamená, že zkopírujete potřebné soubory na serveru a nastavení odpovídající `web.config` soubor, který se dá pokyn webového serveru, jak pro spuštění vaší aplikace.

Proces publikování se liší mezi Visual Studio 2017 a Visual Studio 2015. Konkrétně, Visual Studio 2015 automatizuje některé z kroků, včetně vytváření `web.config`, ale tato automatizace omezuje dlouhodobé flexibility a kontroly. Visual Studio 2017 vyžaduje další ruční kroky, ale zajišťuje přesnější kontrolu nad prostředí Pythonu. Obě možnosti jsou popsány zde.

> [!Note]
> Informace o změny mezi Visual Studio 2015 a Visual Studio 2017, najdete v blogovém příspěvku, [publikovat do Azure v sadě Visual Studio 2017](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Požadavky

V tomto návodu budete potřebovat projekt webové aplikace založené na rozhraní Bottle, Flask a Django. Pokud ještě nemáte projektu a chtěli vyzkoušet proces publikování, vytvořte jednoduchou testovací projekt následujícím způsobem:

1. V sadě Visual Studio, vyberte **soubor > Nový > projekt**, vyhledejte "Bottle", vyberte **Bottle webový projekt**, zadejte a název a cestu k projektu, klikněte na tlačítko **OK**. (Šablona Bottle je součástí úlohy pro vývoj v Pythonu; viz [instalace](installing-python-support-in-visual-studio.md).)

1. Postupujte podle pokynů k instalaci externích balíčků, že vyberete **nainstalovat do virtuálního prostředí** a základním intepretu upřednostňované virtuálního prostředí. Obvykle odpovídají tato volba verzi Pythonu, které jsou nainstalované ve službě App Service.

1. Testování projektu místně stisknutím klávesy F5 nebo výběrem **ladit > Spustit ladění**.

## <a name="create-an-azure-app-service"></a>Vytvoření služby Azure App Service

Publikování na platformě Azure, je požadován cíl služby App Service. K tomuto účelu můžete vytvořit služby App Service pomocí předplatného Azure nebo můžete použít dočasný Web.

Pokud ještě nemáte předplatné, začněte tématem [bezplatný účet Azure úplné](https://azure.microsoft.com/free/), což zahrnuje velkorysá kredity pro služby Azure. Také zvažte [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), kterým získáte kredit 25 USD měsíčně za celý rok.

> [!Tip]
> I když vyzve k zadání platební kartu k ověření svého účtu Azure, se neúčtuje karty. Můžete také nastavit [limit útraty](/azure/billing/billing-spending-limit) rovna vaše bezplatné kredity k zajištění, že dojde k žádné další poplatky. Kromě toho Azure nabízí free služby App Service úroveň plánu, který je ideální pro aplikace jednoduchý test, jak je popsáno v další části.

### <a name="using-a-subscription"></a>Pomocí předplatného

S aktivní předplatné Azure vytvořte službu App Service s prázdnou webovou aplikaci následujícím způsobem:

1. Přihlaste se na [portal.azure.com](https://portal.azure.com).
1. Vyberte **+ nová**a pak vyberte **Web + mobilní zařízení** následovaný **webovou aplikaci**.
1. Zadejte název webové aplikace, ponechejte **skupiny prostředků** "Vytvořit nový" a zvolte **Windows** jako operační systém.
1. Vyberte **plán App service/umístění**vyberte **vytvořit nový**a zadejte název a umístění. Potom vyberte **cenová úroveň**, přejděte dolů a vyberte **F1 Free** plánovat, stiskněte klávesu **vyberte**následovaný **OK** a potom **Vytvořit**.
1. (Volitelné) Po vytvoření služby App Service přejít k němu, vyberte **získat profil publikování**a uložte si soubor .CSR místně.

### <a name="using-a-temporary-app-service"></a>Pomocí dočasného služby App Service

Vytvořte dočasný službu App Service bez předplatného Azure následujícím způsobem:

1. Otevřete prohlížeč, abyste [try.azurewebsites.net](https://try.azurewebsites.net).
1. Vyberte **webovou aplikaci** typ aplikace vyberte **Další**.
1. Vyberte **prázdný web**následovaný **vytvořit**.
1. Přihlaste se pomocí přihlášení prostřednictvím sociální sítě podle vašeho výběru a po krátkou dobu je připraven na zobrazenou adresu URL vašeho webu.
1. Vyberte **stáhnout profil publikování** a uložit `.publishsettings` souboru, který můžete použít později.

## <a name="configure-python-on-azure-app-service"></a>Konfigurace Pythonu ve službě Azure App Service

Jakmile budete mít služby App Service s prázdnou webovou aplikací běžící (buď v rámci vašeho předplatného, nebo na bezplatné webu), nainstalujte zvolené verzi jazyka Python, jak je popsáno [Správa Pythonu ve službě Azure App Service](managing-python-on-azure-app-service.md). Publikování ze sady Visual Studio 2017, zaznamenejte přesnou cestu k interpretu Pythonu nainstalována s rozšířením webu, jak je popsáno v tomto článku.

V případě potřeby můžete také nainstalovat `bottle` balíček pomocí procesu v těchto pokynech, protože tento balíček nainstaluje jako součást jiné kroky v tomto názorném postupu.

## <a name="publish-to-app-service---visual-studio-2017"></a>Publikování do služby App Service – Visual Studio 2017

Publikování do služby Azure App Service ze sady Visual Studio 2017 kopií pouze soubory v projektu na serveru. Je proto nutné, vytvořit soubory potřebné ke konfiguraci prostředí serveru.

1. V **Průzkumníku řešení** sady Visual Studio klikněte pravým tlačítkem na projekt a vyberte **Přidat > Nová položka**. V zobrazeném dialogovém okně vyberete šablonu "Web.config pro Azure (Fast CGI)" a vyberte OK. Tím se vytvoří `web.config` souboru v kořenovém adresáři projektu.

1. Upravit `PythonHandler` záznam v `web.config` tak, aby cesta odpovídá instalaci Pythonu na serveru (naleznete v tématu [odkaz Konfigurace služby IIS](https://www.iis.net/configreference) (iis.net) najdete přesné informace). Například pro Python 3.6.1 x64 položka by měla vypadat následovně:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Nastavte `WSGI_HANDLER` záznam v `web.config` podle potřeby pro architekturu používáte:

    - **Bottle**: Přidat závorky po `app.wsgi_app` jak je znázorněno níže. To je nezbytné, protože tento objekt je funkce (viz `app.py`) namísto proměnné:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: Změnit `WSGI_HANDLER` hodnota, která se `<project_name>.app` kde `<project_name>` odpovídá názvu vašeho projektu. Můžete najít přesně identifikátor pohledem `from <project_name> import app` příkaz v `runserver.py`. Například pokud má projekt název "FlaskAzurePublishExample", položka bude vypadat takto:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: Dvě změny, které jsou potřeba k `web.config` pro projekty v Django. Nejprve změňte `WSGI_HANDLER` hodnota, která se `django.core.wsgi.get_wsgi_application()` (objekt je ve `wsgi.py` souboru):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Za druhé, přidejte následující položku níže pro `WSGI_HANDLER`a nahraďte `DjangoAzurePublishExample` s názvem vašeho projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Jenom aplikace Django**: V projektu Django `settings.py` přidejte domény adresy URL webu do `ALLOWED_HOSTS` jak je znázorněno níže, nahradíte ".net vspython-test-02.azurewebsites" adresu URL a samozřejmě:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Nepodařilo se přidat adresu URL svého výsledky do pole chyby "DisallowedHost na / neplatné záhlaví HTTP_HOST:"\<URL webu\>". Budete muset přidat "\<URL webu\>" k ALLOWED_HOSTS. "

    Pamatujte, že pokud je pole prázdné, Django umožňuje automaticky "localhost", ale přidáte vaše adresa URL výroby odebere této funkce. Pro kopie z tohoto důvodu můžete chtít udržovat samostatnou vývoje a provozu `settings.py`, nebo použít proměnné prostředí pro řízení běhu hodnoty.

1. V **Průzkumníka řešení**, rozbalte složku se stejným názvem jako váš projekt, klikněte pravým tlačítkem myši `static` složky, vyberte **Přidat > Nová položka...** , vyberte šablonu "Azure statických souborů web.config" a vyberte **OK**. Tato akce vytvoří další `web.config` v `static` složku, která zakáže zpracování pro složky Pythonu. Tato konfigurace odesílá požadavky pro statické soubory výchozí webový server, než pomocí aplikace v Pythonu.

1. Uložte projekt, pak v sadě Visual Studio **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **publikovat**.

    ![Publikování příkazu v místní nabídce projektu](media/template-web-publish-command.png)

1. V **publikovat** kartu, která se zobrazí, vyberte cíl publikování:

    a. Ve vlastním předplatném Azure: vyberte **Microsoft Azure App Service**, pak **vybrat existující** následovaný **publikovat**. Zobrazí se dialogové okno, ve kterém můžete vybrat odpovídající předplatné a služby app service. Pokud není zobrazená služby App Service, použijte stažený profil publikování, jak je popsáno níže pro dočasné službu APp Service.

    ![Publikování do Azure – krok 1, Visual Studio 2017 na stávající předplatná](media/tutorials-common-publish-1a-2017.png)

    b. Pokud používáte dočasné služby App Service na try.azurewebsites.net nebo jinak budete muset použít profil publikování, vyberte **>** ovládacího prvku najít **importovat profil**, vyberte tuto možnost, pak Vyberte **publikovat**. Tento parametr vyzve k zadání umístění `.publishsettings` soubor předtím stáhli.

    ![Publikování do Azure – krok 1, Visual Studio 2017, dočasné app service](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio zobrazí stav publikování v okně "Web publikovat aktivity" a v okně Publikovat. Po dokončení publikování se otevře výchozí prohlížeč na adresu URL webu. Adresa URL se také zobrazí v okně Publikovat.

1. Když se otevře v prohlížeči, může se zobrazit zpráva, "na stránce nelze zobrazit, protože došlo k vnitřní chybě serveru." Tato zpráva znamená, že vaše prostředí Python na serveru není úplně nakonfigurovaný, v takovém případě postupujte takto:

    a. Odkazovat na akci [Správa Pythonu ve službě Azure App Service](managing-python-on-azure-app-service.md), ujistěte se, že máte odpovídající rozšíření nainstalované na webu Pythonu.

    b. Zkontrolujte cestu k interpretu Pythonu ve vašich `web.config` souboru. Cesta musí přesně odpovídat umístění pro instalaci zvolený server rozšíření.

    c. Upgradovat všechny balíčky uvedené ve vaší aplikaci pomocí konzoly Kudu `requirements.txt` souboru: přejděte do stejné složky Pythonu, který se používá v `web.config`, jako například `/home/python361x64`, a spusťte následující příkaz, jak je popsáno v [KonzolaKudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console)části:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Pokud se zobrazí chyby oprávnění při spuštění tohoto příkazu, zkontrolujte, že používáte příkaz ve složce rozšíření lokality a *není* ve složce instalace Pythonu výchozí služby App Service. Protože nelze upravit tyto výchozí prostředí, pokus o instalaci balíčků jistě selže.

    d. Podrobné informace o chybě výstupu, přidejte následující řádek do `web.config` v rámci `<system.webServer>` uzlu, který poskytuje podrobnější chybový výstup:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Zkuste restartovat App Service po instalaci nové balíčky. Restart je nezbytný, při změně `web.config`, jak služby App Service nepodporuje automatické restartování vždy, když `web.config` změny.

    > [!Tip]
    > Pokud provedete změny do vaší aplikace `requirements.txt` souboru, je nutné znovu pomocí konzoly Kudu nainstalovat všechny balíčky, které jsou teď uvedené v tomto souboru.

1. Jakmile dokončíte konfiguraci serverového prostředí, aktualizujte stránku v prohlížeči. Měla by se zobrazit webová aplikace.

    ![Výsledky publikování aplikace Bottle, Flask a Django do služby App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikování do služby App Service – Visual Studio 2015

> [!Note]
> Krátké video tohoto procesu můžete najít na [Pythonu pro Visual Studio tento kurz: Vytváření webu](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (webu youtube.com, 3m10s).

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt vyberte **publikovat**.

1. V **publikovat** dialogového okna, vyberte **Microsoft Azure App Service**:

  ![Publikování do Azure – krok 1](media/tutorials-common-publish-1.png)

1. Vyberte cílovou třídu:

    - Pokud máte předplatné Azure, vyberte **Microsoft Azure App Service** jako cíl publikování v následujícím dialogovém okně vyberte stávající službu App Service nebo vyberte **nový** vytvořit nový certifikát.
    - Pokud používáte dočasný web z try.azurewebsites.net, vyberte **Import** jako cíl publikování, pak vyhledat `.publishsettings` soubor stáhnout z webu a vyberte **OK**.

1. Podrobnosti služby App Service se zobrazí v **publikovat** dialogového okna **připojení** kartu níže.

  ![Publikování do Azure – krok 2](media/tutorials-common-publish-2.png)

1. Vyberte **Další >** podle potřeby a zkontrolujte další nastavení.

1. Vyberte **publikovat**. Aplikaci nasadíte do Azure a váš výchozí prohlížeč otevře na dané lokalitě.

Jako součást tohoto procesu Visual Studio také provede následující kroky:

- Vytvoření `web.config` souboru na serveru, který obsahuje příslušné odkazy na aplikace `wsgi_app` fungovat a do služby App Service výchozí Python 3.4 překladač.
- Vypnout zpracování souborů v projektu `static` složky (pravidla pro tento `web.config`).
- Virtuální prostředí publikujte na server.
- Přidat `web.debug.config` Souborová služba a ptvsd ladicí nástroje vám umožní povolit vzdálené ladění.

Jak bylo uvedeno dříve, postup automatického zjednodušení procesu publikování, ale to ztížit řízení prostředí Pythonu. Například `web.config` soubor je vytvořen pouze na serveru, ale nebyl přidán do projektu. Proces publikování také trvá déle, protože to je kopírování celé virtuální prostředí z vývojového počítače spíše než spoléhání se na konfiguraci serveru.

Nakonec můžete chtít spravovat vlastní `web.config` a `requirements.txt` přímo udržovat balíčků na serveru. Pomocí `requirements.txt`, zejména záruky, které prostředí vývoje a server vždy odpovídat.
