---
title: Konfigurace role pro cloudové služby Azure
description: Zjistěte, jak vytvořit a nakonfigurovat role pro Azure cloud services pomocí sady Visual Studio.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410044"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurace rolí cloudové služby Azure v sadě Visual Studio
Cloudové služby Azure může mít jednu nebo více pracovních procesů nebo webové role. Pro každou roli budete muset definovat, jak nastavit tuto roli a také nakonfigurovat tak, jak tuto roli běží. Další informace o rolích v cloudových službách najdete v tématu [Úvod do Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Informace pro cloudové služby jsou uloženy v následující soubory:

- **ServiceDefinition. csdef** – definiční soubor služby definuje nastavení modulu runtime pro vaši cloudovou službu, včetně toho, jaké role jsou povinné, koncové body a velikost virtuálního počítače. Žádná data uložená v `ServiceDefinition.csdef` nelze změnit, pokud je vaše role spuštěna.
- **ServiceConfiguration. cscfg** – konfigurační soubor služby nakonfiguruje, kolik instancí role je spuštěno, a hodnoty nastavení definované pro roli. Data uložená v `ServiceConfiguration.cscfg` lze změnit i v případě, že vaše role běží.

Pokud chcete uchovávat různé hodnoty pro nastavení, které řídí vykonávání roli, můžete definovat více konfigurací služby. Pro jednotlivá prostředí nasazení můžete použít konfiguraci jinou službu. Můžete třeba nastavit připojovací řetězec účtu úložiště pomocí emulátoru lokálního úložiště Azure v místní službě konfigurace a vytvořit další konfigurace služby pro použití služby Azure storage v cloudu.

Při vytváření cloudové služby Azure v sadě Visual Studio dvou konfiguracích služby se automaticky vytvořen a přidán do projektu Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurace cloudové služby Azure
Cloudové služby Azure z Průzkumníka řešení v sadě Visual Studio, můžete nakonfigurovat, jak je znázorněno v následujícím postupu:

1. Vytvořte nebo otevřete v sadě Visual Studio projekt cloudové služby Azure.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte možnost **vlastnosti**.

    ![Místní nabídky projektu Průzkumníka řešení](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stránce Vlastnosti projektu vyberte kartu **vývoj** .

    ![Stránka Vlastnosti projektu - karta vývoj](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. V seznamu **Konfigurace služby** vyberte název konfigurace služby, kterou chcete upravit. (Pokud chcete provést změny u všech konfigurací služby pro tuto roli, vyberte možnost **všechny konfigurace**.)

    > [!IMPORTANT]
    > Pokud se rozhodnete specifické konfigurace služby, některé vlastnosti jsou zakázané, protože jejich lze nastavit pouze u všech konfigurací. Chcete-li tyto vlastnosti upravit, je nutné vybrat možnost **všechny konfigurace**.
    >
    >

    ![Seznam konfiguraci služby pro cloudové služby Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Změňte počet instancí role
Pro zlepšení výkonu cloudové služby, můžete změnit počet instancí role, které jsou spuštěny na základě počtu uživatelů nebo zatížení, byl očekáván pro určité role. Samostatný virtuální počítač se vytvoří pro každou instanci role při spuštění cloudové služby v Azure. To ovlivní fakturaci pro nasazení této cloudové služby. Další informace o fakturaci najdete v tématu [vysvětlení faktury za Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Vytvořte nebo otevřete v sadě Visual Studio projekt cloudové služby Azure.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Řešení Explorer Azure role kontextové nabídky](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Konfigurace** .

    ![Karta Konfigurace](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Konfigurace služby seznamu](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Do textového pole **počet instancí** zadejte počet instancí, které chcete pro tuto roli spustit. Každá instance běží na samostatném virtuálním počítači, při publikování cloudové služby v Azure.

    ![Aktualizuje se počet instancí](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Správa připojovací řetězce pro účty úložiště
Můžete přidat, odebrat nebo změnit připojovací řetězce pro konfiguraci služby. Například můžete chtít místní připojovací řetězec pro konfiguraci místní služby, která má hodnotu `UseDevelopmentStorage=true`. Můžete také nakonfigurovat konfigurací cloudové služby, který používá účet úložiště v Azure.

> [!WARNING]
> Po zadání klíče údaje účtu úložiště Azure pro připojovací řetězec účtu úložiště se tyto informace se ukládají místně v konfiguračním souboru služby. Tyto informace není aktuálně uložený jako šifrovaný text.
>
>

Když použijete jinou hodnotu pro každou konfiguraci služby, není nutné používat jinými řetězci připojení v cloudové službě nebo upravit kód při publikování vaší cloudové služby v Azure. Můžete použít stejný název pro připojovací řetězec v kódu a hodnota se liší v závislosti na konfiguraci služby, který vyberete při vytváření cloudové služby nebo při jejím publikování.

1. Vytvořte nebo otevřete v sadě Visual Studio projekt cloudové služby Azure.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Řešení Explorer Azure role kontextové nabídky](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Nastavení** .

    ![Karta nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Konfigurace služby](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pokud chcete přidat připojovací řetězec, vyberte **Přidat nastavení**.

    ![Přidat připojovací řetězec](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Jakmile toto nové nastavení je přidaný do seznamu, aktualizujte řádek v seznamu potřebné informace.

    ![Nový připojovací řetězec](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Název** – zadejte název, který chcete použít pro připojovací řetězec.
    - V rozevíracím seznamu **typ** vyberte **připojovací řetězec** .
    - **Hodnota** – můžete buď zadat připojovací řetězec přímo do buňky **hodnoty** , nebo vybrat tři tečky (...) pro práci v dialogovém okně **vytvořit připojovací řetězec úložiště** .

1. V dialogovém okně **vytvořit připojovací řetězec úložiště** vyberte možnost **připojit pomocí**. Postupujte podle pokynů pro zvolené možnosti:

    - **Microsoft Azure emulátor úložiště** – Pokud vyberete tuto možnost, zbývající nastavení v dialogovém okně budou zakázaná, protože se vztahují jenom na Azure. Vyberte **OK**.
    - **Vaše předplatné** – Pokud vyberete tuto možnost, použijte rozevírací seznam k výběru a přihlášení do účet Microsoft nebo přidejte účet Microsoft. Vyberte předplatné a úložiště účtu Azure. Vyberte **OK**.
    - **Ručně zadané přihlašovací údaje** – zadejte název účtu úložiště a buď primární, nebo druhý klíč. Vyberte možnost **připojení** (protokol HTTPS se doporučuje pro většinu scénářů). Vyberte **OK**.

1. Pokud chcete odstranit připojovací řetězec, vyberte připojovací řetězec a pak vyberte **odebrat nastavení**.

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="programmatically-access-a-connection-string"></a>Programový přístup k připojovací řetězec

Následující kroky ukazují, jak programově přistupovat k připojovací řetězec pomocí jazyka C#.

1. Přidejte následující direktivy using do souboru C# ve kterém chcete použít nastavení:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Následující kód ukazuje příklad toho, jak přistupovat k připojovací řetězec. Nahraďte zástupný text &lt;connectionStringName > odpovídající hodnotou.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Přidat vlastní nastavení pro použití v Azure cloudové služby
Vlastní nastavení v konfiguračním souboru služby umožňují přidat název a hodnotu řetězce pro specifické konfigurace služby. Můžete pomocí tohoto nastavení můžete konfigurovat funkce v cloudové službě čtení hodnoty nastavení a použití této hodnoty pro řízení logiku z vašeho kódu. Tyto hodnoty konfigurace služby můžete změnit bez nutnosti znovu sestavovat služby balíčku nebo při spuštění cloudové služby. Kód můžete zkontrolovat oznámení při změně nastavení. Viz [RoleEnvironment. měnící se událost](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Můžete přidat, odebrat nebo upravit vlastní nastavení pro konfiguraci služby. Jiné hodnoty může být vhodné pro tyto řetězce pro jiné služby konfigurace.

Když použijete jinou hodnotu pro každou konfiguraci služby, není nutné používat různé řetězce v cloudové službě nebo upravit kód při publikování vaší cloudové služby v Azure. Můžete použít stejný název pro řetězec v kódu a hodnota se liší v závislosti na konfiguraci služby, který vyberete při vytváření cloudové služby nebo při jejím publikování.

1. Vytvořte nebo otevřete v sadě Visual Studio projekt cloudové služby Azure.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Řešení Explorer Azure role kontextové nabídky](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Nastavení** .

    ![Karta nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Konfigurace služby seznamu](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pokud chcete přidat vlastní nastavení, vyberte **Přidat nastavení**.

    ![Přidat vlastní nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Jakmile toto nové nastavení je přidaný do seznamu, aktualizujte řádek v seznamu potřebné informace.

    ![Nové vlastní nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Název** – zadejte název nastavení.
    - V rozevíracím seznamu **typ** vyberte **řetězec** .
    - **Hodnota** – zadejte hodnotu nastavení. Můžete buď zadat hodnotu přímo do buňky **hodnoty** , nebo vybrat tři tečky (...) a zadat hodnotu do dialogového okna **Upravit řetězec** .

1. Pokud chcete odstranit vlastní nastavení, vyberte nastavení a pak vyberte **odebrat nastavení**.

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programový přístup k nastavení vlastní hodnoty

Následující kroky ukazují, jak získat programově přístup k vlastní nastavení pomocí jazyka C#.

1. Přidejte následující direktivy using do souboru C# ve kterém chcete použít nastavení:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Následující kód ukazuje příklad toho, jak přistupovat k vlastní nastavení. Nahraďte zástupný text &lt;ho nastavení > odpovídající hodnotou.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Spravovat místní úložiště pro každou instanci role
Můžete přidat místní soubor úložiště v systému pro každou instanci role. Data uložená v tom, že úložiště není přístupný ostatních instancí role, pro který jsou data uložená, nebo jiné role.

1. Vytvořte nebo otevřete v sadě Visual Studio projekt cloudové služby Azure.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Řešení Explorer Azure role kontextové nabídky](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **místní úložiště** .

    ![Karta místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. V seznamu **Konfigurace služby** se ujistěte, že je vybraná možnost **všechny konfigurace** , protože nastavení místního úložiště platí pro všechny konfigurace služby. Jakákoli jiná hodnota výsledkem všech vstupních polí na stránce, protože se zakázalo.

    ![Konfigurace služby seznamu](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Pokud chcete přidat položku místního úložiště, vyberte **Přidat místní úložiště**.

    ![Přidat místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po přidání nové položky místního úložiště do seznamu aktualizujte řádek v seznamu potřebné informace.

    ![Nová položka místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Název** – zadejte název, který chcete použít pro nové místní úložiště.
    - **Velikost (MB)** – zadejte velikost v MB, kterou potřebujete pro nové místní úložiště.
    - **Vyčistit při recyklaci role** – tuto možnost vyberte, pokud chcete data z nového místního úložiště odebrat, když se virtuální počítač role recykluje.

1. Pokud chcete položku místního úložiště odstranit, vyberte ji a pak vyberte **Odebrat místní úložiště**.

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="programmatically-accessing-local-storage"></a>Programově přístup k místnímu úložišti

Tato část ukazuje, jak programově získat přístup k místnímu úložišti pomocí C# zápisu textového souboru testu `MyLocalStorageTest.txt`.

### <a name="write-a-text-file-to-local-storage"></a>Zápis do textového souboru do místního úložiště

Následující kód ukazuje příklad toho, jak zápis do textového souboru do místního úložiště. Nahraďte zástupný text &lt;LocalStorageName > odpovídající hodnotou.

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

### <a name="find-a-file-written-to-local-storage"></a>Najít soubor se zapisují do místního úložiště

Chcete-li zobrazit soubor vytvořený kódem v předchozí části, postupujte podle těchto kroků:

1. V oznamovací oblasti systému Windows klikněte pravým tlačítkem myši na ikonu Azure a v místní nabídce vyberte možnost **Zobrazit uživatelské rozhraní emulátoru COMPUTE**.

    ![Zobrazit emulátoru služby výpočty v Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Vyberte webovou roli.

    ![Emulátor výpočtů v Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. V nabídce **Microsoft Azure emulátor COMPUTE** vyberte **nástroje** > **otevřít místní úložiště**.

    ![Položka nabídky otevřít místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otevření okna Průzkumníka Windows zadejte do textového pole **hledání** text ' MyLocalStorageTest. txt ' a výběrem **ENTER** spusťte hledání.

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o projektech Azure v aplikaci Visual Studio čtením [konfigurace projektu Azure](vs-azure-tools-configuring-an-azure-project.md). Další informace o schématu cloudové služby najdete v tématu [Přehled schématu](https://msdn.microsoft.com/library/azure/dd179398).
