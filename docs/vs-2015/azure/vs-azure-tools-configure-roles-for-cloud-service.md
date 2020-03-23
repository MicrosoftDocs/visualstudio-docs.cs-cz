---
title: Konfigurace rolí pro cloudovou službu Azure
description: Přečtěte si, jak nastavit a nakonfigurovat role pro cloudové služby Azure pomocí Visual Studia.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 810ebfcfb4cb4354c3df4c0d9892a37ca1624256
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302579"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurace rolí cloudové služby Azure v sadě Visual Studio
Cloudová služba Azure může mít jednu nebo více pracovních nebo webových rolí. Pro každou roli je třeba definovat, jak je tato role nastavena, a také nakonfigurovat způsob, jakým je tato role spuštěna. Další informace o rolích v cloudových službách najdete ve videu [Úvod do Cloudových služeb Azure](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Informace pro cloudovou službu jsou uloženy v následujících souborech:

- **ServiceDefinition.csdef** - Soubor definice služby definuje nastavení za běhu pro cloudovou službu, včetně jaké role jsou požadovány, koncové body a velikost virtuálního počítače. Žádná z dat `ServiceDefinition.csdef` uložených v aplikaci nelze změnit, pokud je spuštěna vaše role.
- **ServiceConfiguration.cscfg** - Konfigurační soubor služby konfiguruje, kolik instancí role jsou spuštěny a hodnoty nastavení definované pro roli. Data uložená `ServiceConfiguration.cscfg` v aplikaci lze změnit, když je spuštěna vaše role.

Chcete-li uložit různé hodnoty pro nastavení, která řídí způsob spuštění role, můžete definovat více konfigurací služby. Pro každé prostředí nasazení můžete použít jinou konfiguraci služby. Můžete například nastavit připojovací řetězec účtu úložiště tak, aby používal místní emulátor úložiště Azure v konfiguraci místní služby, a vytvořit jinou konfiguraci služby pro použití úložiště Azure v cloudu.

Když vytvoříte cloudovou službu Azure ve Visual Studiu, automaticky se vytvoří a přidají do vašeho projektu Azure dvě konfigurace služby:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurace cloudové služby Azure
Cloudovou službu Azure můžete nakonfigurovat z Průzkumníka řešení v sadě Visual Studio, jak je znázorněno v následujících krocích:

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a v kontextové nabídce vyberte **příkaz Vlastnosti**.

    ![Kontextová nabídka projektu Průzkumníka řešení](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stránce vlastností projektu vyberte kartu **Vývoj.**

    ![Stránka vlastností projektu – karta Vývoj](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. V seznamu **Konfigurace služby** vyberte název konfigurace služby, kterou chcete upravit. (Pokud chcete provést změny ve všech konfiguracích služeb pro tuto roli, vyberte **možnost Všechny konfigurace**.)

    > [!IMPORTANT]
    > Pokud zvolíte konkrétní konfiguraci služby, některé vlastnosti jsou zakázány, protože je lze nastavit pouze pro všechny konfigurace. Chcete-li tyto vlastnosti upravit, musíte vybrat **možnost Všechny konfigurace**.
    >
    >

    ![Seznam konfigurace služby pro cloudovou službu Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Změna počtu instancí rolí
Chcete-li zlepšit výkon cloudové služby, můžete změnit počet instancí role, které jsou spuštěny, na základě počtu uživatelů nebo zatížení očekávané pro konkrétní roli. Samostatný virtuální počítač se vytvoří pro každou instanci role, když cloudová služba běží v Azure. To má vliv na fakturaci pro nasazení této cloudové služby. Další informace o fakturaci najdete [v tématu Vysvětlení faktury za Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**rozbalte uzel projektu. V uzlu **Role** klikněte pravým tlačítkem myši na roli, kterou chcete aktualizovat, a v místní nabídce vyberte **vlastnosti**.

    ![Kontextová nabídka role Azure průzkumníka řešení](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Configuration** (Konfigurace).

    ![Karta Konfigurace](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Seznam konfigurace služby](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Do textového pole **Počet instancí** zadejte počet instancí, které chcete pro tuto roli spustit. Každá instance běží na samostatném virtuálním počítači při publikování cloudové služby do Azure.

    ![Aktualizace počtu instancí](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. V panelu nástrojů Visual Studio vyberte **Uložit**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Správa připojovacích řetězců pro účty úložiště
Pro konfigurace služeb můžete přidávat, odebírat nebo upravovat připojovací řetězce. Můžete například chtít místní připojovací řetězec pro konfiguraci `UseDevelopmentStorage=true`místní služby, která má hodnotu . Můžete také nakonfigurovat konfiguraci cloudové služby, která používá účet úložiště v Azure.

> [!WARNING]
> Když zadáte informace o klíči účtu úložiště Azure pro připojovací řetězec účtu úložiště, tyto informace se uloží místně v konfiguračním souboru služby. Tyto informace však nejsou aktuálně uloženy jako šifrovaný text.
>
>

Při použití jiné hodnoty pro každou konfiguraci služby není nutné používat různé připojovací řetězce ve vaší cloudové službě nebo upravovat kód při publikování cloudové služby do Azure. Můžete použít stejný název pro připojovací řetězec v kódu a hodnota se liší, v závislosti na konfiguraci služby, kterou vyberete při vytváření cloudové služby nebo při publikování.

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**rozbalte uzel projektu. V uzlu **Role** klikněte pravým tlačítkem myši na roli, kterou chcete aktualizovat, a v místní nabídce vyberte **vlastnosti**.

    ![Kontextová nabídka role Azure průzkumníka řešení](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Settings** (Nastavení).

    ![Karta Nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Konfigurace služby](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Chcete-li přidat připojovací řetězec, vyberte **Přidat nastavení**.

    ![Přidání připojovacího řetězce](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po přidání nového nastavení do seznamu aktualizujte řádek v seznamu potřebnými informacemi.

    ![Nový připojovací řetězec](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Název** - Zadejte název, který chcete použít pro připojovací řetězec.
    - **Typ** : V rozevíracím seznamu vyberte **připojovací řetězec.**
    - **Hodnota** - Můžete buď zadat připojovací řetězec přímo do **buňky Hodnota,** nebo vybrat tři tečky (...) pro práci v dialogovém okně **Vytvořit připojovací řetězec úložiště.**

1. V dialogovém okně **Vytvořit připojovací řetězec úložiště** vyberte možnost připojit **pomocí**aplikace . Potom postupujte podle pokynů pro vybranou možnost:

    - **Emulátor úložiště Microsoft Azure** – Pokud vyberete tuto možnost, zbývající nastavení v dialogovém okně jsou zakázána, protože se vztahují jenom pro Azure. Vyberte **OK**.
    - **Vaše předplatné** – Pokud vyberete tuto možnost, použijte rozevírací seznam k výběru a přihlášení k účtu Microsoft nebo k přidání účtu Microsoft. Vyberte účet předplatného Azure a úložiště. Vyberte **OK**.
    - **Ručně zadaná pověření** – zadejte název účtu úložiště a primární nebo druhý klíč. Vyberte možnost **připojení** (HTTPS se doporučuje pro většinu scénářů.) Vyberte **OK**.

1. Chcete-li připojovací řetězec odstranit, vyberte připojovací řetězec a pak vyberte **Odebrat nastavení**.

1. V panelu nástrojů Visual Studio vyberte **Uložit**.

## <a name="programmatically-access-a-connection-string"></a>Programově přístup k připojovacímu řetězci

Následující kroky ukazují, jak programově přistupovat k připojovacímu řetězci pomocí jazyka C#.

1. Přidejte následující pomocí direktiv do souboru Jazyka C#, kde budete používat nastavení:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Následující kód ilustruje příklad, jak získat přístup k připojovacímu řetězci. Nahraďte zástupný symbol &lt;ConnectionStringName> příslušnou hodnotou.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Přidání vlastních nastavení, která se použijí ve své cloudové službě Azure
Vlastní nastavení v konfiguračním souboru služby umožňují přidat název a hodnotu řetězce pro konkrétní konfiguraci služby. Toto nastavení můžete použít ke konfiguraci funkce ve cloudové službě tak, že načtete hodnotu nastavení a použijete tuto hodnotu k řízení logiky v kódu. Tyto hodnoty konfigurace služby můžete změnit bez nutnosti znovu sestavit balíček služeb nebo při spuštění cloudové služby. Váš kód může zkontrolovat oznámení o změně nastavení. Viz [RoleEnvironment.Changing Event](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Můžete přidat, odebrat nebo upravit vlastní nastavení konfigurace služby. Můžete chtít různé hodnoty pro tyto řetězce pro různé konfigurace služby.

Při použití jiné hodnoty pro každou konfiguraci služby není nutné používat různé řetězce ve vaší cloudové službě nebo upravovat kód při publikování cloudové služby do Azure. Můžete použít stejný název pro řetězec v kódu a hodnota se liší, v závislosti na konfiguraci služby, kterou vyberete při vytváření cloudové služby nebo při publikování.

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**rozbalte uzel projektu. V uzlu **Role** klikněte pravým tlačítkem myši na roli, kterou chcete aktualizovat, a v místní nabídce vyberte **vlastnosti**.

    ![Kontextová nabídka role Azure průzkumníka řešení](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Settings** (Nastavení).

    ![Karta Nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Seznam konfigurace služby](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Chcete-li přidat vlastní nastavení, vyberte **Přidat nastavení**.

    ![Přidat vlastní nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po přidání nového nastavení do seznamu aktualizujte řádek v seznamu potřebnými informacemi.

    ![Nové vlastní nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Název** - Zadejte název nastavení.
    - **Typ** : V rozevíracím seznamu vyberte **řetězec.**
    - **Hodnota** - Zadejte hodnotu nastavení. Hodnotu můžete zadat přímo do **buňky Hodnota** nebo vybrat tři tečky (...) a zadat hodnotu do dialogového okna **Upravit řetězec.**

1. Chcete-li odstranit vlastní nastavení, vyberte toto nastavení a pak vyberte **Odebrat nastavení**.

1. V panelu nástrojů Visual Studio vyberte **Uložit**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programově přístup k hodnotě vlastního nastavení

Následující kroky ukazují, jak programově přistupovat k vlastnímu nastavení pomocí jazyka C#.

1. Přidejte následující pomocí direktiv do souboru Jazyka C#, kde budete používat nastavení:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Následující kód ilustruje příklad, jak získat přístup k vlastní nastavení. Nahraďte zástupný symbol &lt;SettingName> příslušnou hodnotou.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Správa místního úložiště pro každou instanci role
Pro každou instanci role můžete přidat místní úložiště souborů. Data uložená v tomto úložišti nejsou přístupná jiným iminátorům role, pro kterou jsou data uložena, ani jiným rolím.

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**rozbalte uzel projektu. V uzlu **Role** klikněte pravým tlačítkem myši na roli, kterou chcete aktualizovat, a v místní nabídce vyberte **vlastnosti**.

    ![Kontextová nabídka role Azure průzkumníka řešení](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Místní úložiště.**

    ![Karta Místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. V seznamu **Konfigurace služby** zkontrolujte, zda je vybrána možnost **Všechny konfigurace,** protože nastavení místního úložiště platí pro všechny konfigurace služby. Jakákoli jiná hodnota má za následek zakázání všech vstupních polí na stránce.

    ![Seznam konfigurace služby](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Chcete-li přidat položku místního úložiště, vyberte **Přidat místní úložiště**.

    ![Přidání místního úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po přidání nové položky místního úložiště do seznamu aktualizujte řádek v seznamu potřebnými informacemi.

    ![Nová položka místního úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Název** - Zadejte název, který chcete použít pro nové místní úložiště.
    - **Velikost (MB)** - Zadejte velikost v MB, kterou potřebujete pro nové místní úložiště.
    - **Vyčistit recyklaci rolí** – tuto možnost vyberte, chcete-li odebrat data v novém místním úložišti při recyklaci virtuálního počítače pro roli.

1. Chcete-li odstranit položku místního úložiště, vyberte ji a pak vyberte **Odebrat místní úložiště**.

1. V panelu nástrojů Visual Studio vyberte **Uložit**.

## <a name="programmatically-accessing-local-storage"></a>Programově přístup k místnímu úložišti

Tato část ukazuje, jak programově přistupovat k místnímu úložišti pomocí jazyka C# zápisem testovacího textového souboru `MyLocalStorageTest.txt`.

### <a name="write-a-text-file-to-local-storage"></a>Zápis textového souboru do místního úložiště

Následující kód ukazuje příklad, jak napsat textový soubor do místního úložiště. Nahraďte zástupný symbol &lt;LocalStorageName> příslušnou hodnotou.

```csharp
// Retrieve an object that points to the local storage resource
LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");

//Define the file name and path
string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
String filePath = Path.Combine(paths);

using (FileStream writeStream = File.Create(filePath))
{
    Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
    writeStream.Write(textToWrite, 0, textToWrite.Length);
}
```

### <a name="find-a-file-written-to-local-storage"></a>Vyhledání souboru zapsaného do místního úložiště

Chcete-li zobrazit soubor vytvořený kódem v předchozí části, postupujte takto:

1. V oznamovací oblasti Windows klikněte pravým tlačítkem myši na ikonu Azure a v místní nabídce vyberte **Zobrazit uhlavní nastavení emulátoru výpočetního prostředí**.

    ![Zobrazit výpočetní emulátor Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Vyberte webovou roli.

    ![Výpočetní emulátor Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. V nabídce **Microsoft Azure Compute Emulator** vyberte **Nástroje** > **otevřít místní úložiště**.

    ![Otevřít položku nabídky místního obchodu](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otevření okna Průzkumníka Windows zadejte do textového pole **Hledat** text soubor MyLocalStorageTest.txt a výběrem **možnosti Enter** spusťte hledání.

## <a name="next-steps"></a>Další kroky
Další informace o projektech Azure ve Visual Studiu najdete [v podrobnostech Konfigurace projektu Azure](vs-azure-tools-configuring-an-azure-project.md). Další informace o schématu cloudové služby najdete v části [Odkaz na schéma](https://msdn.microsoft.com/library/azure/dd179398).
