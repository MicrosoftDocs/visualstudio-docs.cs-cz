---
title: Migrace & publikování webové aplikace do služby Azure Cloud Service
description: Zjistěte, jak migrovat a publikovat webovou aplikaci do cloudové služby Azure pomocí Visual Studia
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: a5f918cac9d2b9e97c047e8823d7702768134336
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489672"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Postup: Migrace a publikování webové aplikace do cloudové služby Azure z Visual Studia

Chcete-li využít výhod hostingových služeb a škálování schopnosti Azure, můžete chtít migrovat a nasadit webové aplikace do cloudové služby Azure. Jsou vyžadovány pouze minimální změny. Tento článek popisuje nasazení pouze do cloudových služeb; v aplikaci App Service najdete [v tématu Nasazení webové aplikace ve službě Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Tato migrace je podporována pouze pro konkrétní projekty pracovního postupu ASP.NET, Silverlight, WCF a WCF. Není podporována pro ASP.NET základní projekty. Viz [Podporované šablony projektů](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrace projektu do cloudových služeb

1. Klikněte pravým tlačítkem myši na projekt webové aplikace a vyberte **převést > převést na projekt cloudové služby Microsoft Azure**. (Všimněte si, že tento příkaz se nezobrazí, pokud již máte projekt webové role v řešení.)
1. Visual Studio vytvoří projekt cloudové služby v řešení, které obsahuje požadovanou webovou roli. Název tohoto projektu je stejný jako váš projekt aplikace `.Azure`s plus přípona .
1. Visual Studio také nastaví **Copy Local** vlastnost true pro všechna sestavení, které jsou požadovány pro MVC 2, MVC 3, MVC 4 a Silverlight obchodní aplikace. Tato vlastnost přidá tato sestavení do balíčku služeb, který se používá pro nasazení.

   > [!Important]
   > Pokud máte další sestavení nebo soubory, které jsou požadovány pro tuto webovou aplikaci, je nutné ručně nastavit vlastnosti těchto souborů. Informace o nastavení těchto vlastností naleznete [v tématu Zahrnutí souborů do balíčku služeb](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Chyby a varování

Všechna upozornění nebo chyby, ke kterým dojde, označují problémy, které je třeba opravit před nasazením do Azure, jako jsou chybějící sestavení.

Pokud vytvoříte aplikaci, spustíte ji místně pomocí emulátoru výpočetního prostředí nebo ji publikujete do Azure, může se zobrazit chyba: "Zadaná cesta, název souboru nebo obojí jsou příliš dlouhé." Tato chyba označuje, že délka plně kvalifikovaný název projektu Azure přesahuje 146 znaků. Chcete-li problém opravit, přesuňte řešení do jiné složky s kratší cestou.

Další informace o tom, jak zacházet s upozorněními jako s chybami, najdete [v tématu Konfigurace projektu cloudové služby Azure pomocí sady Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Testování migrace místně

1. V **Průzkumníku řešení**Sady Visual Studio klepněte pravým tlačítkem myši na projekt přidané cloudové služby a vyberte příkaz **Nastavit jako spouštěcí projekt**.
1. Vyberte **ladění > spuštění ladění** (F5) ke spuštění prostředí ladění Azure. Toto prostředí konkrétně poskytuje emulaci různých služeb Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Použití databáze Azure SQL pro vaši aplikaci

Pokud máte připojovací řetězec pro vaši webovou aplikaci, která používá místní databázi SQL Serveru, musíte místo toho migrovat databázi do azure sql database a aktualizovat připojovací řetězec. Pokyny k tomuto procesu naleznete v následujících tématech:

- [Migrace databáze systému SQL Server do služby SQL Database v cloudu](/azure/sql-database/sql-database-cloud-migrate)
- [Pomocí rozhraní .NET (C#) s Visual Studio se můžete připojit a dotazovat a databázi Azure SQL](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publikování aplikace do cloudové služby Azure

1. Vytvořte potřebné účty cloudových služeb a úložišť ve svém předplatném Azure, jak je popsáno v [části Příprava na publikování nebo nasazení aplikace Azure z Visual Studia](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. V Sadě Visual Studio klikněte pravým tlačítkem myši na projekt aplikace a vyberte **Publikovat do Microsoft Azure...** (což se liší od možnosti Publikovat..." .).
1. V **publikování aplikace Azure,** která se zobrazí, přihlaste se pomocí účtu s předplatným Azure a vyberte **další >**.
1. Na kartě **Nastavení > běžná nastavení** vyberte cílovou cloudovou službu z rozevíracího seznamu **Cloudové služby** spolu s vybraným prostředím a konfiguracemi.
1. V **části Nastavení > Upřesnit nastavení**vyberte účet úložiště, který chcete použít, a pak vyberte Další **>**.
1. V **části Diagnostika**zvolte, zda chcete odesílat informace do přehledů aplikací.
1. Chcete-li zobrazit souhrn, vyberte **další >** a pak vyberte **Publikovat** a spusťte nasazení.
1. Visual Studio otevře okno protokolu aktivit, ve kterém můžete sledovat průběh:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Nepovinné) Chcete-li proces nasazení zrušit, klepněte pravým tlačítkem myši na řádkovou položku v protokolu aktivit a zvolte **zrušit a odebrat**. Tento příkaz zastaví proces nasazení a odstraní prostředí nasazení z Azure. Poznámka: Chcete-li odebrat toto prostředí nasazení po jeho nasazení, musíte použít [portál Azure](https://portal.azure.com).
1. (Nepovinné) Po spuštění instancí rolí Visual Studio automaticky zobrazí prostředí nasazení v průzkumníku serveru > uzlu **Cloudservices.** Zde můžete zobrazit stav jednotlivých instancí rolí.
1. Chcete-li získat přístup k vaší aplikaci po nasazení, zvolte šipku vedle vašeho nasazení, když se stav **Dokončeno** zobrazí v **protokolu aktivit Azure** spolu s adresou URL. Podrobnosti o spuštění konkrétního typu webové aplikace z Azure najdete v následující tabulce.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Použití výpočetního emulátoru a spuštění aplikace v Azure

Všechny typy aplikací lze spustit v prohlížeči připojeném k ladicímu programu sady Visual Studio výběrem **možnosti Ladění > Start Ladění** (F5). S ASP.NET prázdný projekt webové aplikace, `.aspx` musíte nejprve přidat stránku v aplikaci a nastavit ji jako úvodní stránku pro váš webový projekt.

Následující tabulka obsahuje podrobnosti o spuštění aplikace v Azure:

| Typ webové aplikace | Běh v Azure |
| --- | --- |
| ASP.NET webová aplikace<br/>(včetně MVC 2, MVC 3, MVC 4) | Vyberte adresu URL na kartě **Nasazení** pro **protokol aktivit Azure**. |
| ASP.NET prázdná webová aplikace | Pokud máte ve `.aspx` své aplikaci výchozí stránku, vyberte adresu URL na kartě **Nasazení** pro **protokol aktivit Azure**. Chcete-li přejít na jinou stránku, zadejte v prohlížeči adresu URL následujícího formuláře:`<deployment_url>/<page_name>.aspx` |
| Aplikace Silverlight<br/>Aplikace Silverlight Business<br/>Navigační aplikace Silverlight | Přejděte na konkrétní stránku aplikace pomocí následujícího formuláře URL:`<deployment_url>/<page_name>.aspx` |
| Aplikace služby WCF<br/>Aplikace služby pracovního postupu WCF | Nastavte `.svc` soubor jako úvodní stránku projektu služby WCF. Poté přejděte na`<deployment_url>/<service_file>.svc` |
| ASP.NET dynamických entit<br/>ASP.NET dynamická data Linq na SQL | Aktualizujte připojovací řetězec, jak je popsáno v další části. Potom přejděte na . `<deployment_url>/<page_name>.aspx` Pro Linq na SQL, musíte použít databázi Azure SQL. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aktualizace připojovacího řetězce pro dynamické entity ASP.NET

1. Vytvořte databázi SQL Azure pro ASP.NET webové entity, jak je popsáno výše v (#use-an-azuresql-database-for-your-application).
1. Přidejte tabulky a pole, které potřebujete pro tuto databázi z webu Azure Portal.
1. Zadejte připojovací řetězec v souboru `web.config` v následujícím formátu a uložte soubor:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    Aktualizujte hodnotu *connectionString* pomocí připojovacího řetězce ADO.NET pro databázi SQL Azure následujícím způsobem:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Podporované šablony projektů

Aplikace, které lze migrovat a publikovat do cloudových služeb, musí používat jednu ze šablon v následující tabulce. ASP.NET Jádro není podporováno.

| Skupina šablon | Šablona projektu |
| --- | --- |
| Web | ASP.NET webová aplikace (rozhraní.NET Framework) |
| Web | ASP.NET Webová aplikace MVC 2 |
| Web | ASP.NET Webová aplikace MVC 3 |
| Web | ASP.NET webová aplikace MVC4 |
| Web | ASP.NET prázdná webová aplikace (nebo web) |
| Web | ASP.NET MVC 2 Prázdná webová aplikace |
| Web | ASP.NET webová aplikace dynamických datových entit |
| Web | ASP.NET webovou aplikaci Dynamic Data Linq do webové aplikace SQL |
| Silverlight | Aplikace Silverlight |
| Silverlight | Aplikace Silverlight Business |
| Silverlight | Navigační aplikace Silverlight |
| WCF | Aplikace služby WCF |
| WCF | Aplikace služby pracovního postupu WCF |
| Pracovní postup | Aplikace služby pracovního postupu WCF |

## <a name="next-steps"></a>Další kroky

- [Příprava na publikování nebo nasazení aplikace Azure z Visual Studia](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Nastavení pojmenovaných ověřovacích pověření](vs-azure-tools-setting-up-named-authentication-credentials.md).
