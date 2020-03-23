---
title: Publikování aplikace Pythonu do služby Azure App Service ve Windows
description: Jak publikovat webovou aplikaci Pythonu přímo do služby Azure App Service ve Windows z Visual Studia, včetně potřebného obsahu pro soubor web.config.
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
ms.openlocfilehash: cf9125476a4fdc369cc22034e081f2151020f064
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784612"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publikování do služby Azure App Service ve Windows

> [!Note]
> Tento obsah a popsané funkce jsou zastaralé, ale pokračovat v práci. Vývojáři Pythonu se vyzývají, aby migrovali do [App Service na Linuxu,](publishing-python-web-applications-to-azure-from-visual-studio.md) kde je to možné.

Visual Studio poskytuje možnost publikovat webovou aplikaci Pythonu přímo do služby Azure App Service ve Windows. Publikování do služby Azure App Service ve Windows znamená zkopírování `web.config` potřebných souborů na server a nastavení příslušného souboru, který instruuje webový server, jak spustit aplikaci.

Proces publikování se liší mezi Visual Studio 2017 a novější a Visual Studio 2015. Konkrétně Visual Studio 2015 automatizuje některé kroky, `web.config`včetně vytvoření , ale tato automatizace omezuje dlouhodobou flexibilitu a řízení. Visual Studio 2017 a novější vyžaduje další ruční kroky, ale poskytuje přesnější kontrolu nad prostředím Pythonu. Obě možnosti jsou popsány zde.

> [!Note]
> Informace o změnách mezi Visual Studio 2015 a Visual Studio 2017 a novějším najdete v příspěvku blogu [Publikovat do Azure ve Visual Studiu 2017](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Požadavky

Pro tento návod potřebujete projekt webové aplikace založený na rámci Bottle, Flask nebo Django. Pokud ještě nemáte projekt a chcete vyzkoušet proces publikování, vytvořte jednoduchý testovací projekt následujícím způsobem:

1. V sadě Visual Studio vyberte **soubor > nový > project**, vyhledejte "Láhev", vyberte webový projekt **láhve**, zadejte a název a cestu k projektu, klepněte na tlačítko **OK**. (Šablona Bottle je součástí vývojovéúlohy Pythonu; viz [Instalace](installing-python-support-in-visual-studio.md).)

1. Podle pokynů nainstalujte externí balíčky a vyberte **instalovat do virtuálního prostředí** a preferovaný základní překladač pro virtuální prostředí. Obvykle odpovídáte této volbě s verzí Pythonu nainstalovanou ve službě App Service.

1. Otestujte projekt místně stisknutím klávesy F5 nebo výběrem **možnosti Ladění > Spustit ladění**.

## <a name="create-an-azure-app-service"></a>Vytvoření služby Azure App Service

Publikování do Azure vyžaduje cílovou službu App Service. Pro tento účel můžete vytvořit službu app pomocí předplatného Azure, nebo můžete použít dočasný web.

Pokud ještě nemáte předplatné, začněte s [bezplatným úplným účtem Azure](https://azure.microsoft.com/free/), který zahrnuje štědré kredity za služby Azure. Zvažte také registraci do [aplikace Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), která vám poskytuje kredit $25 každý měsíc po celý rok.

> [!Tip]
> Přestože Azure požádá o platební kartu k ověření vašeho účtu, karta se neúčtuje. Můžete také nastavit [limit útraty](/azure/billing/billing-spending-limit) rovnající se vašim bezplatným kreditům, abyste zaručili, že nedojde k žádným dalším poplatkům. Kromě toho Azure poskytuje bezplatnou úroveň plánu služby App Service, která je ideální pro jednoduché testovací aplikace, jak je popsáno v další části.

### <a name="using-a-subscription"></a>Použití předplatného

S aktivním předplatným Azure vytvořte službu App Service s prázdnou webovou aplikací takto:

1. Přihlaste se na [portal.azure.com](https://portal.azure.com).
1. Vyberte **+Nový**, pak vyberte **Web + Mobile** následované Web **Appem**.
1. Zadejte název webové aplikace, nechte **skupinu prostředků** na "Vytvořit nový" a jako operační systém zvolte **Windows.**
1. Vyberte **Plán/umístění služby App**, vyberte **Vytvořit nový**a zadejte název a umístění. Pak vyberte **Cenovou úroveň**, přejděte dolů a vyberte plán **F1 Free,** stiskněte **Vybrat**, následovaný **OK** a pak **Vytvořit**.
1. (Nepovinné) Po vytvoření služby App Service přejděte na něj, vyberte **Získat profil publikování**a uložte soubor místně.

### <a name="using-a-temporary-app-service"></a>Použití dočasné služby App Service

Vytvořte dočasnou službu App Service bez nutnosti předplatného Azure následujícím způsobem:

1. Otevřete prohlížeč, [chcete-li try.azurewebsites.net](https://try.azurewebsites.net).
1. Vyberte **Web App** pro typ aplikace a pak vyberte **Další**.
1. Vyberte **Možnost Prázdný web**, následovanou **položkou Vytvořit**.
1. Přihlaste se pomocí sociálního přihlášení dle vašeho výběru a po krátké době je váš web připraven na zobrazené adrese URL.
1. Vyberte **Stáhnout profil** `.publishsettings` publikování a soubor, který použijete později, uložte.

## <a name="configure-python-on-azure-app-service"></a>Konfigurace Pythonu ve službě Azure App Service

Jakmile budete mít spuštěnou službu App Service s prázdnou webovou aplikací (buď ve vašem předplatném, nebo na bezplatném webu), nainstalujte vybranou verzi Pythonu, jak je popsáno [ve správě Pythonu ve službě Azure App Service](managing-python-on-azure-app-service.md). Pro publikování z Visual Studia 2017 a novější, zaznamenat přesnou cestu k překladudu Pythonu nainstalován s rozšířením webu, jak je popsáno v tomto článku.

V případě potřeby můžete `bottle` balíček nainstalovat také pomocí procesu v těchto pokynech, protože tento balíček je nainstalován jako součást dalších kroků v tomto návodu.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Publikování do služby App Service – Visual Studio 2017 a novější

Publikování do služby Azure App Service z Visual Studia 2017 a novější zkopíruje jenom soubory v projektu na server. Je proto nutné vytvořit potřebné soubory pro konfiguraci prostředí serveru.

1. V **Průzkumníkovi řešení**Sady Visual Studio klepněte pravým tlačítkem myši na projekt a vyberte **přidat > novou položku...**. V dialogovém okně, které se zobrazí, vyberte šablonu "Azure web.config (Fast CGI)" a vyberte OK. Tím se v kořenovém adresáři vašeho projektu vytvoří soubor `web.config`.

1. Upravte `PythonHandler` položku v režimu `web.config` tak, aby cesta odpovídala instalaci Pythonu na serveru (přesné podrobnosti naleznete v [tématu Odkaz na konfiguraci služby IIS](https://www.iis.net/configreference) (iis.net). Například pro Python 3.6.1 x64 by se měla položka zobrazit takto:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Nastavte `WSGI_HANDLER` položku `web.config` podle potřeby pro rámec, který používáte:

    - **Láhev:** přidejte závorky, `app.wsgi_app` jak je znázorněno níže. To je nezbytné, protože tento `app.py`objekt je funkce (viz) spíše než proměnná:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Baňka** `WSGI_HANDLER` : `<project_name>.app` Změňte hodnotu na místo, kde `<project_name>` se shoduje s názvem projektu. Můžete najít přesný identifer při `from <project_name> import app` pohledu `runserver.py`na prohlášení v . Například pokud projekt s názvem "FlaskAzurePublishExample", položka se zobrazí takto:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: Pro projekty Django jsou zapotřebí `web.config` dvě změny. Nejprve změňte `WSGI_HANDLER` `django.core.wsgi.get_wsgi_application()` hodnotu na (objekt je v souboru): `wsgi.py`

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Za druhé, přidejte následující `WSGI_HANDLER`položku `DjangoAzurePublishExample` pod položku pro , která nahradí název projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Pouze aplikace Django**: V `settings.py` souboru projektu Django přidejte doménu URL webu, `ALLOWED_HOSTS` jak je uvedeno níže, a nahraďte "vspython-test-02.azurewebsites.net" adresou URL, samozřejmě:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Pokud nepřidáte adresu URL do pole, dojde k chybě "DisallowedHost at / Invalid HTTP_HOST header: '\<url\>webu ". K ALLOWED_HOSTS může\<být\>nutné přidat adresu URL webu."

    Všimněte si, že když je pole prázdné, Django automaticky povolí "localhost", ale přidání matné adresy URL této produkce tuto možnost odstraní. Z tohoto důvodu můžete chtít udržovat samostatné `settings.py`vývojové a výrobní kopie , nebo použít proměnné prostředí k řízení hodnot doby běhu.

1. V **Průzkumníku řešení**rozbalte složku s názvem stejný `static` jako váš projekt, klikněte pravým tlačítkem myši na složku, vyberte **přidat > novou položku...**, vyberte šablonu "Azure static files web.config" a vyberte **OK**. Tato akce ve složce `static` vytvoří další soubor `web.config`, který pro tuto složku zakáže zpracování Pythonu. Tato konfigurace odesílá požadavky na statické soubory na výchozí webový server, a ne do aplikace Python.

1. Uložte projekt a potom v **Průzkumníku řešení**sady Visual Studio klepněte pravým tlačítkem myši na projekt a vyberte **publikovat**.

    ![Příkaz Publikovat v kontextové nabídce projektu](media/template-web-publish-command.png)

1. Na kartě **Publikovat,** která se zobrazí, vyberte cíl publikování:

    a. Vaše vlastní předplatné Azure: vyberte **Microsoft Azure App Service**, pak **vyberte existující** následovaný **publish**. Zobrazí se dialogové okno, ve kterém můžete vybrat příslušné předplatné a službu aplikace. Pokud se služba App Service nezobrazí, použijte stažený profil publikování, jak je popsáno níže pro dočasnou službu APp.

    ![Publikování do Azure krok 1, Visual Studio 2017 a novější, existující předplatná](media/tutorials-common-publish-1a-2017.png)

    b. Pokud používáte dočasnou službu App Service na try.azurewebsites.net nebo jinak **>** potřebujete použít profil publikování, vyberte ovládací prvek pro **nahledání profilu importu**, vyberte tuto možnost a pak vyberte **Publikovat**. Zobrazí se výzva k `.publishsettings` umístění dříve staženého souboru.

    ![Publikování do Azure krok 1, Visual Studio 2017 a novější, dočasná aplikační služba](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio zobrazuje stav publikování v okně Aktivita publikování na webu a v okně Publikovat. Po dokončení publikování se na adrese URL webu otevře výchozí prohlížeč. Adresa URL se také zobrazí v okně Publikovat.

1. Po otevření prohlížeče se může zobrazit zpráva "Stránku nelze zobrazit, protože došlo k chybě interního serveru." Tato zpráva označuje, že vaše prostředí Pythonu na serveru není plně nakonfigurováno, v takovém případě proveďte následující kroky:

    a. Znovu se podívejte [na Správa Pythonu ve službě Azure App Service](managing-python-on-azure-app-service.md)a ujistěte se, že máte nainstalované příslušné rozšíření webu Pythonu.

    b. Zkontrolujte cestu k překladaci `web.config` Pythonu v souboru. Cesta se musí přesně shodovat s umístěním instalace vybraného rozšíření webu.

    c. Pomocí konzole `requirements.txt` Kudu můžete upgradovat všechny balíčky uvedené v souboru aplikace: přejděte do stejné složky Pythonu, která se používá v `web.config`aplikaci , například `/home/python361x64`, a spusťte následující příkaz popsaný v části konzole [Kudu:](managing-python-on-azure-app-service.md#azure-app-service-kudu-console)

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Pokud se při spuštění tohoto příkazu zobrazí chyby oprávnění, zkontrolujte, zda používáte příkaz ve složce rozšíření webu a *ne* ve složce jedné z výchozích instalací App Service v Pythonu. Vzhledem k tomu, že tato výchozí prostředí nelze změnit, pokus o instalaci balíčků se jistě nezdaří.

    d. Pro podrobný výstup chyby přidejte následující řádek `web.config` do uzlu, `<system.webServer>` který poskytuje podrobnější výstup chyby:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Zkuste restartovat službu App Service po instalaci nových balíčků. Restartování není nutné při `web.config`změně , jako App `web.config` Service provádí automatické restartování při každé změně.

    > [!Tip]
    > Pokud v souboru `requirements.txt` vaší aplikace provedete nějaké změny, nezapomeňte opět pomocí konzoly Kudu nainstalovat všechny balíčky uvedené v tomto souboru.

1. Jakmile dokončíte konfiguraci serverového prostředí, aktualizujte stránku v prohlížeči. Měla by se zobrazit webová aplikace.

    ![Výsledky publikování aplikací Bottle, Flask a Django ve službě App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikování na službu App Service – Visual Studio 2015

> [!Note]
> Krátké video tohoto procesu lze nalézt na [Visual Studio Python Tutorial: Budování webových stránek](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3m10s).

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt vyberte **publikovat**.

1. V dialogovém okně **Publikovat** vyberte **službu Microsoft Azure App Service**:

  ![Publikování do Azure krok 1](media/tutorials-common-publish-1.png)

1. Vyberte cíl:

    - Pokud máte předplatné Azure, vyberte jako cíl publikování **službu Microsoft Azure App Service,** pak v následujícím dialogovém okně vyberte existující službu App Service nebo vyberte **Nový** a vytvořte novou.
    - Pokud používáte dočasný web z try.azurewebsites.net, vyberte **Importovat** jako `.publishsettings` cíl publikování, vyhledejte soubor stažený z webu a vyberte **OK**.

1. Podrobnosti služby App Service se zobrazí na kartě **Připojení** v dialogovém okně **Publikování** níže.

  ![Publikování do Azure krok 2](media/tutorials-common-publish-2.png)

1. Podle potřeby vyberte **Další >,** abyste zkontrolovali další nastavení.

1. Vyberte **Publikovat**. Po nasazení aplikace do Azure se na tomto webu otevře výchozí prohlížeč.

V rámci tohoto procesu Visual Studio také provede následující kroky:

- Vytvořte `web.config` soubor na serveru, který obsahuje příslušné `wsgi_app` ukazatele na funkci aplikace a na výchozí překladač Pythonu 3.4 služby App Service.
- Vypněte zpracování souborů ve `static` složce projektu (pravidla pro `web.config`toto jsou v ).
- Publikujte virtuální prostředí na server.
- Přidejte `web.debug.config` soubor a nástroje pro ladění ptvsd, které umožňují vzdálené ladění.

Jak již bylo uvedeno dříve, tyto automatické kroky zjednodušují proces publikování, ale ztěžují řízení prostředí Pythonu. `web.config` Soubor je například vytvořen pouze na serveru, ale není přidán do projektu. Proces publikování také trvá déle, protože kopíruje celé virtuální prostředí z vývojového počítače, nikoli spoléhání se na konfiguraci serveru.

Nakonec můžete chtít udržovat svůj `web.config` vlastní `requirements.txt` soubor a použít k údržbě balíčků na serveru přímo. Použití `requirements.txt`, zejména zaručuje, že vývoj a serverprostředí vždy odpovídat.
