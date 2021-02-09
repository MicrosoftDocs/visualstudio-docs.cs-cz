---
title: Publikování aplikace v Pythonu pro Azure App Service ve Windows
description: Postup publikování webové aplikace v Pythonu přímo do Azure App Service ve Windows ze sady Visual Studio, včetně potřebného obsahu pro soubor web.config.
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
ms.openlocfilehash: af3e7c2d74a9d7b3a95ae24bba37981822247728
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912552"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publikování do Azure App Service ve Windows

> [!Note]
> Tento obsah a popsané funkce jsou zastaralé, ale fungují i nadále. Vývojářům v Pythonu doporučujeme migrovat na [App Service na Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) , pokud je to možné.

Visual Studio poskytuje možnost publikovat webovou aplikaci v Pythonu přímo do Azure App Service ve Windows. Publikování do Azure App Service ve Windows znamená kopírování potřebných souborů na server a nastavení vhodného `web.config` souboru, který dává pokyn webovému serveru k tomu, jak aplikaci spustit.

Proces publikování se mezi Visual Studio 2017 a novějším a Visual Studio 2015 liší. Konkrétně Visual Studio 2015 automatizuje některé kroky, včetně vytvoření `web.config` , ale tato automatizace omezuje dlouhodobou flexibilitu a kontrolu. Visual Studio 2017 a novější vyžaduje více ručních kroků, ale poskytuje přesnější kontrolu nad prostředím Pythonu. Obě možnosti jsou popsány zde.

> [!Note]
> Další informace o změnách mezi Visual Studio 2015 a Visual Studio 2017 a novějším najdete v blogovém příspěvku [publikování do Azure v aplikaci Visual studio 2017](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Požadavky

Pro tento návod potřebujete projekt webové aplikace založený na láhvi, baňce nebo Djangoch architekturách. Pokud projekt ještě nemáte a chcete vyzkoušet proces publikování, vytvořte jednoduchý testovací projekt následujícím způsobem:

1. V aplikaci Visual Studio vyberte **soubor > nový > projekt**, vyhledejte "láhev", vyberte **webový projekt láhve**, zadejte název a název a cestu k projektu, vyberte **OK**. (Šablona láhve je součástí úlohy vývoje v Pythonu; viz [instalace](installing-python-support-in-visual-studio.md).)

1. Podle zobrazených výzev nainstalujte externí balíčky, vyberte možnost **nainstalovat do virtuálního prostředí** a preferovaný základní překladač pro virtuální prostředí. Obvykle se tato volba shoduje s verzí Pythonu nainstalovanou na App Service.

1. Otestujte projekt místně stisknutím klávesy F5 nebo výběrem možnosti **ladění > spustit ladění**.

## <a name="create-an-azure-app-service"></a>Vytvoření služby Azure App Service

Publikování do Azure vyžaduje cílový App Service. Pro tento účel můžete vytvořit App Service pomocí předplatného Azure nebo můžete použít dočasnou lokalitu.

Pokud ještě nemáte předplatné, začněte s [bezplatným úplným účtem Azure](https://azure.microsoft.com/free/), který zahrnuje kredity velkorysá pro služby Azure. Zvažte také registraci [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), což vám poskytne $25 kredit každý měsíc po celý rok.

> [!Tip]
> I když Azure vyžaduje platební kartu k ověření vašeho účtu, karta se neúčtuje. Můžete také nastavit [limit útraty](/azure/billing/billing-spending-limit) , který se rovná vašim bezplatným kreditům, aby se zaručilo, že nedojde k žádným dalším poplatkům. Azure navíc poskytuje bezplatnou úroveň plánu App Service, která je ideální pro jednoduché testovací aplikace, jak je popsáno v následující části.

### <a name="using-a-subscription"></a>Použití předplatného

S aktivním předplatným Azure vytvořte App Service s prázdnou webovou aplikací, a to následujícím způsobem:

1. Přihlaste se na [Portal.Azure.com](https://portal.azure.com).
1. Vyberte **+ Nový** a pak **web a mobilní zařízení** a potom vyberte **Webová aplikace**.
1. Zadejte název webové aplikace, ponechte **skupinu prostředků** na vytvořit novou a jako operační systém zvolte **Windows** .
1. Vyberte **plán/umístění služby App Service**, vyberte **vytvořit novou** a zadejte název a umístění. Pak vyberte **cenovou úroveň**, přejděte dolů k a vyberte plán **zdarma F1** , stiskněte **Vybrat**, potom klikněte na **OK** a pak na **vytvořit**.
1. Volitelné Po vytvoření App Service přejděte na ni, vyberte **získat profil publikování** a uložte soubor místně.

### <a name="using-a-temporary-app-service"></a>Použití dočasné App Service

Vytvořte dočasné App Service, aniž byste potřebovali předplatné Azure, a to následujícím způsobem:

1. Otevřete prohlížeč na [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/) .
1. Jako typ aplikace vyberte **Webová aplikace** a pak vyberte **Další**.
1. Vyberte **prázdné pracoviště** a potom **vytvořit**.
1. Přihlaste se přes sociální přihlášení podle vašeho výběru a po krátké době, kdy je lokalita připravena na zobrazené adrese URL.
1. Vyberte **Stáhnout profil publikování** a uložte `.publishsettings` soubor, který použijete později.

## <a name="configure-python-on-azure-app-service"></a>Konfigurace Pythonu na Azure App Service

Jakmile máte App Service s prázdnou webovou aplikací spuštěnou (buď ve vašem předplatném, nebo na bezplatném webu), nainstalujte si zvolenou verzi Pythonu, která je popsána v tématu [Správa Pythonu v Azure App Service](managing-python-on-azure-app-service.md). Pro publikování ze sady Visual Studio 2017 nebo novější zaznamenejte přesnou cestu k interpretu Pythonu nainstalovanému s rozšířením lokality, jak je popsáno v tomto článku.

V případě potřeby můžete balíček nainstalovat také `bottle` pomocí procesu v těchto pokynech, protože tento balíček je nainstalován jako součást dalších kroků v tomto návodu.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Publikování do App Service – Visual Studio 2017 a novější

Publikování do Azure App Service ze sady Visual Studio 2017 a novější zkopíruje pouze soubory v projektu na server. Proto je nutné vytvořit potřebné soubory pro konfiguraci prostředí serveru.

1. V aplikaci Visual Studio **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt a vyberte **Přidat > nová položka...**. V zobrazeném dialogovém okně vyberte šablonu "Azure web.config (Fast CGI)" a vyberte OK. Tím se v kořenovém adresáři vašeho projektu vytvoří soubor `web.config`.

1. Upravte `PythonHandler` položku v `web.config` , aby cesta odpovídala instalaci Pythonu na serveru (podrobné informace najdete v tématu Referenční dokumentace ke [konfiguraci služby IIS](https://www.iis.net/configreference) (IIS.NET)). Například pro Python 3.6.1 x64 by se měla položka zobrazit takto:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Nastavte `WSGI_HANDLER` položku v závislosti na používaném `web.config` rozhraní:

    - **Láhev**: přidejte závorky po `app.wsgi_app` následujícím obrázku. To je nezbytné, protože tento objekt je funkce (viz `app.py` ) místo proměnné:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Baňka**: změňte `WSGI_HANDLER` hodnotu na `<project_name>.app` , kde se `<project_name>` shoduje s názvem vašeho projektu. Přesný identifikátorem najdete na základě `from <project_name> import app` příkazu v `runserver.py` . Například pokud má projekt název "FlaskAzurePublishExample", položka by se zobrazila takto:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: pro projekty Django jsou potřeba dvě změny `web.config` . Nejprve změňte `WSGI_HANDLER` hodnotu na `django.core.wsgi.get_wsgi_application()` (objekt je v `wsgi.py` souboru):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Za druhé přidejte následující položku pro `WSGI_HANDLER` , nahraďte `DjangoAzurePublishExample` názvem projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Jenom aplikace Django**: v souboru projektu Django `settings.py` přidejte doménu URL webu do, `ALLOWED_HOSTS` jak je znázorněno níže, a nahraďte ' vspython-test-02.azurewebsites.NET ' adresou URL, samozřejmě:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Při přidání vaší adresy URL do pole dojde k chybě "DisallowedHost on/invalid HTTP_HOST Header: ' \<site URL\> '. Je možné, že budete muset přidat ' \<site URL\> ' do ALLOWED_HOSTS. "

    Všimněte si, že pokud je pole prázdné, Django automaticky povoluje "localhost", ale přidání vaší produkční adresy URL tyto možnosti odebere. Z tohoto důvodu můžete chtít zachovat samostatné vývojové a produkční kopie `settings.py` nebo použít proměnné prostředí k řízení hodnot doby běhu.

1. V **Průzkumník řešení** rozbalte složku s názvem stejné jako váš projekt, klikněte pravým tlačítkem na `static` složku, vyberte **Přidat > nová položka...**, vyberte šablonu "Azure static Files web.config" a vyberte **OK**. Tato akce ve složce `static` vytvoří další soubor `web.config`, který pro tuto složku zakáže zpracování Pythonu. Tato konfigurace odesílá požadavky na statické soubory na výchozí webový server, a ne do aplikace Python.

1. Uložte projekt, potom v aplikaci Visual Studio **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt a vyberte **publikovat**.

    ![Příkaz publikovat v místní nabídce projektu](media/template-web-publish-command.png)

1. Na kartě **publikovat** , která se zobrazí, vyberte cíl publikování:

    a. Vaše vlastní předplatné Azure: vyberte **Microsoft Azure App Service** a pak **Vyberte existující** a potom **publikovat**. Zobrazí se dialogové okno, ve kterém můžete vybrat příslušné předplatné a službu App Service. Pokud se App Service nezobrazí, použijte stažený profil publikování, jak je popsáno níže v tématu dočasná služba APp Service.

    ![Publikování do Azure Step 1, Visual Studio 2017 a novější, existující předplatná](media/tutorials-common-publish-1a-2017.png)

    b. Pokud používáte dočasné App Service v try.azurewebsites.net nebo pokud potřebujete použít profil publikování, vyberte **>** ovládací prvek pro vyhledání **profilu importu**, vyberte tuto možnost a pak vyberte **publikovat**. Zobrazí se výzva k umístění `.publishsettings` souboru staženého dříve.

    ![Publikování do Azure Step 1, Visual Studio 2017 a novější, dočasná App Service](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio zobrazí stav publikování v okně aktivita publikování webu a okno Publikovat. Po dokončení publikování se výchozí prohlížeč otevře na adrese URL webu. Adresa URL je také zobrazena v okně Publikovat.

1. Když se prohlížeč otevře, může se zobrazit zpráva "stránku nelze zobrazit, protože došlo k vnitřní chybě serveru." Tato zpráva znamená, že vaše prostředí Python na serveru není zcela nakonfigurované. v takovém případě proveďte následující kroky:

    a. Přečtěte si znovu o [správě Pythonu v Azure App Service](managing-python-on-azure-app-service.md)a ujistěte se, že máte nainstalované příslušné rozšíření webu Python.

    b. Dvakrát ověřte cestu k interpretu Pythonu v `web.config` souboru. Cesta musí přesně odpovídat umístění instalace zvoleného rozšíření webu.

    c. Pomocí konzoly Kudu Upgradujte všechny balíčky uvedené v souboru vaší aplikace `requirements.txt` : přejděte do stejné složky Pythonu, která se používá v `web.config` , například `/home/python361x64` a spusťte následující příkaz, jak je popsáno v části [Konzola Kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) :

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Pokud při spuštění tohoto příkazu dojde k chybám oprávnění, zkontrolujte, že jste spustili příkaz ve složce rozšíření webu, a *ne* ve složce jedné z App Service výchozích instalací Pythonu. Vzhledem k tomu, že tato výchozí prostředí nemůžete změnit, neproběhne pokus o instalaci balíčků.

    d. Pro podrobný výstup chyby přidejte následující řádek do `web.config` `<system.webServer>` uzlu, který poskytuje podrobnější výstup chyby:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Po instalaci nových balíčků zkuste restartovat App Service. Restart není při změně nutný `web.config` , protože App Service automatické restartování při každé `web.config` změně.

    > [!Tip]
    > Pokud v souboru `requirements.txt` vaší aplikace provedete nějaké změny, nezapomeňte opět pomocí konzoly Kudu nainstalovat všechny balíčky uvedené v tomto souboru.

1. Jakmile dokončíte konfiguraci serverového prostředí, aktualizujte stránku v prohlížeči. Měla by se zobrazit webová aplikace.

    ![Výsledky publikování aplikací Bottle, Flask a Django ve službě App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikování do App Service – Visual Studio 2015

> [!Note]
> Krátké video o tomto procesu najdete v [kurzu Pythonu pro Visual Studio: vytváření webů](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (YouTube.com, 3m10s).

1. V **Průzkumníku řešení** klikněte pravým tlačítkem na požadovaný projekt a vyberte **Publikovat**.

1. V dialogovém okně **publikovat** vyberte **Microsoft Azure App Service**:

  ![Publikovat do Azure – krok 1](media/tutorials-common-publish-1.png)

1. Vyberte cíl:

    - Pokud máte předplatné Azure, vyberte jako cíl publikování možnost **Microsoft Azure App Service** a potom v následujícím dialogovém okně vyberte existující App Service nebo vyberte **Nový** a vytvořte nový.
    - Pokud používáte dočasnou lokalitu z try.azurewebsites.net, vyberte **importovat** jako cíl publikování a pak vyhledejte `.publishsettings` soubor stažený z webu a vyberte **OK**.

1. Podrobnosti App Service se zobrazí na kartě **připojení** dialogového okna **publikovat** níže.

  ![Publikování do Azure Step 2](media/tutorials-common-publish-2.png)

1. V případě potřeby vyberte **další >** pro kontrolu dalších nastavení.

1. Vyberte **Publikovat**. Po nasazení aplikace do Azure se výchozí prohlížeč otevře v této lokalitě.

V rámci tohoto procesu Visual Studio také provádí následující kroky:

- Vytvořte `web.config` na serveru soubor, který obsahuje odpovídající ukazatele na `wsgi_app` funkci aplikace a App Service výchozí interpret Python 3,4.
- Vypnutí zpracování souborů ve `static` složce projektu (pravidla pro tuto funkci jsou v `web.config` ).
- Publikujte virtuální prostředí na server.
- Přidejte `web.debug.config` soubor a ladicí nástroje pro povolení vzdáleného ladění. Pro Visual Studio 2019 verze 16,4 a starší jsou ladicí nástroje ptvsd. Pro Visual Studio 2019 verze 16,5 a novější jsou ladicí nástroje debugpy.

Jak bylo uvedeno dříve, tyto automatické kroky zjednodušují proces publikování, ale obtížně ovládají prostředí Pythonu. Například `web.config` soubor je vytvořen pouze na serveru, ale není přidán do projektu. Proces publikování také trvá déle, protože kopíruje celé virtuální prostředí z vývojového počítače, ale nespoléhá se na konfiguraci serveru.

Nakonec budete chtít zachovat vlastní `web.config` soubor a použít `requirements.txt` ho k údržbě balíčků na serveru přímo. `requirements.txt`Konkrétně je zaručeno, že se vaše vývojové a serverové prostředí vždy shodují.
