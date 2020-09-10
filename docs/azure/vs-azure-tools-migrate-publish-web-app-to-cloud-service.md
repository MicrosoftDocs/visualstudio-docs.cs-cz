---
title: Migrace a publikování webové aplikace do cloudové služby
description: Naučte se migrovat a publikovat webovou aplikaci do cloudové služby Azure pomocí sady Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 06b283e7382fc135e3cd327db0200622de4f5228
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89739978"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Postupy: migrace a publikování webové aplikace do cloudové služby Azure ze sady Visual Studio

Aby bylo možné využívat služby hostování a škálování možností Azure, můžete chtít migrovat a nasazovat webovou aplikaci do cloudové služby Azure. Vyžadují se jenom minimální změny. Tento článek se zabývá nasazením jenom pro cloudové služby. App Service najdete v tématu [nasazení webové aplikace v Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Tato migrace je podporována pouze pro konkrétní projekty pracovního postupu ASP.NET, WCF a WCF. Pro ASP.NET Core projekty není podporována. Viz článek [podporované šablony projektů](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrace projektu na cloudové služby

1. Klikněte pravým tlačítkem myši na uzel řešení a vyberte **přidat > nový projekt...** a přidejte do stávajícího řešení nový projekt **cloudové služby Azure (Classic)** .
1. V dialogovém okně **nový Microsoft Azure cloudová služba (Classic)** klikněte na OK bez přidání rolí do projektu.
1. V nově přidaném Cloud Services projektu klikněte pravým tlačítkem na uzel role a vyberte **Přidat projekt webové role v řešení...**.
1. V dialogu **přidružit k projektu role** vyberte projekt, který chcete přidružit jako webovou roli.

   > [!Important]
   > Máte-li další sestavení nebo soubory, které jsou požadovány pro tuto webovou aplikaci, je nutné ručně nastavit vlastnosti těchto souborů. Informace o tom, jak tyto vlastnosti nastavit, najdete v tématu [zahrnutí souborů do balíčku služby](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Chyby a upozornění

Všechna upozornění a chyby, ke kterým dojde, označují problémy, které se mají opravit před nasazením do Azure, například chybějící sestavení.

Pokud sestavíte aplikaci, spustíte ji místně pomocí emulátoru služby COMPUTE nebo ji publikujete do Azure, může se zobrazit chyba: Zadaná cesta, název souboru nebo obojí jsou příliš dlouhé. Tato chyba označuje, že délka plně kvalifikovaného názvu projektu Azure překračuje 146 znaků. Chcete-li tento problém vyřešit, přesuňte řešení do jiné složky s kratší cestou.

Další informace o tom, jak zacházet s upozorněními jako s chybami, najdete v tématu [konfigurace projektu cloudové služby Azure pomocí sady Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Místní testování migrace

1. V sadě Visual Studio **Průzkumník řešení**klikněte pravým tlačítkem myši na přidaný projekt cloudové služby a vyberte **nastavit jako spouštěný projekt**.
1. Vyberte **ladit > spustit ladění** (F5) a spusťte ladicí prostředí Azure. Toto prostředí konkrétně zajišťuje emulaci různých služeb Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Použití Azure SQL Database pro vaši aplikaci

Pokud máte připojovací řetězec pro webovou aplikaci, která používá místní databázi SQL Server, je nutné místo toho migrovat databázi do Azure SQL Database a aktualizovat připojovací řetězec. Pokyny k tomuto procesu najdete v následujících tématech:

- [Migrace databáze systému SQL Server do služby SQL Database v cloudu](/azure/sql-database/sql-database-cloud-migrate)
- [Použijte .NET (C#) se sadou Visual Studio pro připojení a dotazování a Azure SQL Database](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publikování aplikace do cloudové služby Azure

1. Vytvořte potřebné cloudové služby a účty úložiště v předplatném Azure, jak je popsáno v tématu [Příprava k publikování nebo nasazení aplikace Azure ze sady Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. V aplikaci Visual Studio klikněte pravým tlačítkem na projekt aplikace a vyberte **publikovat do Microsoft Azure...** (to se liší od "publikovat...". příkaz.).
1. V části **publikovat aplikaci Azure** , která se zobrazí, se přihlaste pomocí účtu s vaším předplatným Azure a vyberte **Další >**.
1. Na kartě **nastavení > společná nastavení** vyberte cílovou cloudovou službu z rozevíracího seznamu **cloudová služba** společně s vybraným prostředím a konfiguracemi.
1. V **nastavení > Upřesnit nastavení**vyberte účet úložiště, který se má použít, a pak vyberte **Další >**.
1. V nástroji **Diagnostika**vyberte, zda chcete Application Insights odeslat informace.
1. Vyberte **další >** pro zobrazení souhrnu a pak vyberte **publikovat** a spusťte nasazení.
1. Visual Studio otevře okno protokolu aktivit, kde můžete sledovat průběh:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. Volitelné Proces nasazení zrušíte tak, že kliknete pravým tlačítkem myši na položku řádku v protokolu aktivit a kliknete na **zrušit a odebrat**. Tento příkaz zastaví proces nasazení a odstraní prostředí nasazení z Azure. Poznámka: Chcete-li odebrat toto prostředí nasazení po nasazení, je nutné použít [Azure Portal](https://portal.azure.com).
1. Volitelné Po spuštění instancí rolí Visual Studio automaticky zobrazí prostředí nasazení v uzlu **Průzkumník serveru > Cloud Services** . Tady můžete zobrazit stav jednotlivých instancí rolí.
1. Pro přístup k aplikaci po nasazení klikněte na šipku vedle vašeho nasazení, jakmile se stav **dokončeno** zobrazí v **protokolu aktivit Azure** společně s adresou URL. Podrobnosti o tom, jak spustit konkrétní typ webové aplikace z Azure, najdete v následující tabulce.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Použití výpočetní emulátoru a spuštění aplikace v Azure

Všechny typy aplikací můžete spustit v prohlížeči připojeném k ladicímu programu sady Visual Studio tak, že vyberete **ladění > spustit ladění** (F5). V případě ASP.NET prázdného projektu webové aplikace musíte nejprve `.aspx` do aplikace přidat stránku a nastavit ji jako úvodní stránku pro webový projekt.

Následující tabulka uvádí podrobnosti o spuštění aplikace v Azure:

| Typ webové aplikace | Běžící v Azure |
| --- | --- |
| Webová aplikace ASP.NET<br/>(včetně MVC 2, MVC 3, MVC 4) | Vyberte adresu URL na kartě **nasazení** v **protokolu aktivit Azure**. |
| Prázdná webová aplikace ASP.NET | Pokud máte `.aspx` ve své aplikaci výchozí stránku, vyberte adresu URL v **protokolu aktivit Azure**na kartě **nasazení** . Pokud chcete přejít na jinou stránku, zadejte adresu URL následujícího formuláře v prohlížeči: `<deployment_url>/<page_name>.aspx` |
| Aplikace služby WCF<br/>Aplikace služby pracovního postupu WCF | Nastavte `.svc` soubor jako úvodní stránku pro váš projekt služby WCF. Pak přejděte na `<deployment_url>/<service_file>.svc` |
| ASP.NET dynamické entity<br/>ASP.NET dynamická data LINQ to SQL | Aktualizujte připojovací řetězec, jak je popsáno v následující části. Pak přejděte na `<deployment_url>/<page_name>.aspx` . V případě technologie LINQ to SQL je nutné použít databázi SQL Azure. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aktualizace připojovacího řetězce pro dynamické entity ASP.NET

1. Vytvořte databázi SQL Azure pro webovou aplikaci ASP.NET Dynamic Entities, jak je popsáno výše v tématu (#use-a-azuresql-Database-for-the-Application).
1. Přidejte tabulky a pole, které potřebujete pro tuto databázi, z Azure Portal.
1. V souboru zadejte připojovací řetězec `web.config` s následujícím formátem a soubor uložte:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    Aktualizujte hodnotu *ConnectionString* pomocí připojovacího řetězce ADO.NET pro vaši databázi SQL Azure následujícím způsobem:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Podporované šablony projektů

Aplikace, které je možné migrovat a publikovat do Cloud Services, musí používat jednu ze šablon v následující tabulce. ASP.NET Core se nepodporuje.

| Skupina šablon | Šablona projektu |
| --- | --- |
| Web | ASP.NET webová aplikace (.NET Framework) |
| Web | Webová aplikace ASP.NET MVC 2 |
| Web | Webová aplikace ASP.NET MVC 3 |
| Web | Webová aplikace ASP.NET MVC4 |
| Web | Prázdná webová aplikace ASP.NET (nebo Web) |
| Web | Prázdná webová aplikace ASP.NET MVC 2 |
| Web | Webová aplikace entit dynamických dat ASP.NET |
| Web | Webová aplikace LINQ do SQL ASP.NET Dynamic Data |
| WCF | Aplikace služby WCF |
| WCF | Aplikace služby pracovního postupu WCF |
| Pracovní postup | Aplikace služby pracovního postupu WCF |

## <a name="next-steps"></a>Další kroky

- [Příprava k publikování nebo nasazení aplikace Azure ze sady Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Nastavování přihlašovacích údajů s názvem ověřování](vs-azure-tools-setting-up-named-authentication-credentials.md).
