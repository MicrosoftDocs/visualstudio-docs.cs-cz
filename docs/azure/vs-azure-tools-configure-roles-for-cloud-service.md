---
title: Konfigurace rolí pro cloudovou službu Azure
description: Naučte se, jak nastavit a nakonfigurovat role pro Azure Cloud Services pomocí sady Visual Studio.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: d90567e86d782a64f42f7fdbd06f295a5f130b3a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280860"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurace rolí cloudové služby Azure v sadě Visual Studio
Cloudová služba Azure může mít jednu nebo víc pracovních rolí nebo webových rolí. Pro každou roli musíte definovat způsob nastavení této role a také nakonfigurovat, jak se tato role spouští. Další informace o rolích v cloudových službách najdete v tématu [Úvod do Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Informace pro cloudovou službu jsou uloženy v následujících souborech:

- **ServiceDefinition. csdef** – definiční soubor služby definuje nastavení modulu runtime pro cloudovou službu, včetně toho, jaké role jsou povinné, koncové body a velikost virtuálního počítače. Žádná data uložená v nástroji `ServiceDefinition.csdef` se nedají změnit, když je vaše role spuštěná.
- **ServiceConfiguration. cscfg** – konfigurační soubor služby nakonfiguruje, kolik instancí role je spuštěno, a hodnoty nastavení definované pro roli. Data uložená v nástroji je `ServiceConfiguration.cscfg` možné změnit v době, kdy je vaše role spuštěná.

Chcete-li uložit různé hodnoty pro nastavení, která řídí spouštění rolí, můžete definovat více konfigurací služby. Pro každé prostředí nasazení můžete použít jinou konfiguraci služby. Například můžete nastavit připojovací řetězec účtu úložiště tak, aby používal místní emulátor úložiště Azure v konfiguraci místní služby, a vytvořit další konfiguraci služby pro použití Azure Storage v cloudu.

Když vytvoříte cloudovou službu Azure v aplikaci Visual Studio, automaticky se vytvoří a přidají do projektu Azure dvě konfigurace služby:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurace cloudové služby Azure
Cloudovou službu Azure můžete nakonfigurovat z Průzkumník řešení v aplikaci Visual Studio, jak je znázorněno v následujícím postupu:

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte možnost **vlastnosti**.

    ![Místní nabídka Průzkumník řešeního projektu](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stránce Vlastnosti projektu vyberte kartu **vývoj** .

    ![Stránka vlastností projektu – karta vývoj](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. V seznamu **Konfigurace služby** vyberte název konfigurace služby, kterou chcete upravit. (Pokud chcete provést změny u všech konfigurací služby pro tuto roli, vyberte možnost **všechny konfigurace**.)

    > [!IMPORTANT]
    > Pokud zvolíte určitou konfiguraci služby, některé vlastnosti jsou zakázané, protože je možné je nastavit jenom pro všechny konfigurace. Chcete-li tyto vlastnosti upravit, je nutné vybrat možnost **všechny konfigurace**.

    ![Seznam konfigurací služby pro cloudovou službu Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Změna počtu instancí rolí
Chcete-li zlepšit výkon cloudové služby, můžete změnit počet instancí role, které jsou spuštěny, na základě počtu uživatelů nebo zatížení očekávaného pro určitou roli. Pro každou instanci role se vytvoří samostatný virtuální počítač, když se cloudová služba spustí v Azure. To má vliv na fakturaci za nasazení této cloudové služby. Další informace o fakturaci najdete v tématu [vysvětlení faktury za Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Místní nabídka Průzkumník řešení role Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Configuration** (Konfigurace).

    ![Karta konfigurace](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Seznam konfigurací služby](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Do textového pole **počet instancí** zadejte počet instancí, které chcete pro tuto roli spustit. Každá instance se spouští na samostatném virtuálním počítači, když publikujete cloudovou službu do Azure.

    ![Aktualizuje se počet instancí.](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Správa připojovacích řetězců pro účty úložiště
Můžete přidat, odebrat nebo upravit připojovací řetězce pro konfigurace služby. Například můžete chtít místní připojovací řetězec pro konfiguraci místní služby, která má hodnotu `UseDevelopmentStorage=true` . Možná budete chtít nakonfigurovat taky konfiguraci cloudové služby, která používá účet úložiště v Azure.

> [!WARNING]
> Když zadáte informace o klíči účtu úložiště Azure pro připojovací řetězec účtu úložiště, ukládají se tyto informace místně do konfiguračního souboru služby. Tyto informace se ale v tuto chvíli neukládají jako šifrovaný text.
>
>

Při použití jiné hodnoty pro každou konfiguraci služby nemusíte v cloudové službě používat jiné připojovací řetězce ani upravovat kód při publikování cloudové služby do Azure. Můžete použít stejný název připojovacího řetězce ve vašem kódu a hodnota se liší v závislosti na konfiguraci služby, kterou jste vybrali při vytváření cloudové služby nebo při jejím publikování.

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Místní nabídka Průzkumník řešení role Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Settings** (Nastavení).

    ![Karta nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Konfigurace služby](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pokud chcete přidat připojovací řetězec, vyberte **Přidat nastavení**.

    ![Přidat připojovací řetězec](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po přidání nového nastavení do seznamu aktualizujte řádek v seznamu s potřebnými informacemi.

    ![Nový připojovací řetězec](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Název** – zadejte název, který chcete použít pro připojovací řetězec.
    - V rozevíracím seznamu **typ** vyberte **připojovací řetězec** .
    - **Hodnota** – můžete buď zadat připojovací řetězec přímo do buňky **hodnoty** , nebo vybrat tři tečky (...) pro práci v dialogovém okně **vytvořit připojovací řetězec úložiště** .

1. V dialogovém okně **vytvořit připojovací řetězec úložiště** vyberte možnost **připojit pomocí**. Pak postupujte podle pokynů pro vybranou možnost:

    - **Microsoft Azure emulátor úložiště** – Pokud vyberete tuto možnost, zbývající nastavení v dialogovém okně budou zakázaná, protože se vztahují jenom na Azure. Vyberte **OK**.
    - **Vaše předplatné** – Pokud vyberete tuto možnost, použijte rozevírací seznam k výběru a přihlášení do účet Microsoft nebo přidejte účet Microsoft. Vyberte předplatné Azure a účet úložiště. Vyberte **OK**.
    - **Ručně zadané přihlašovací údaje** – zadejte název účtu úložiště a buď primární, nebo druhý klíč. Vyberte možnost **připojení** (protokol HTTPS se doporučuje pro většinu scénářů). Vyberte **OK**.

1. Pokud chcete odstranit připojovací řetězec, vyberte připojovací řetězec a pak vyberte **odebrat nastavení**.

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="programmatically-access-a-connection-string"></a>Programový přístup k připojovacímu řetězci

Následující kroky ukazují, jak programově přistupovat k připojovacímu řetězci pomocí jazyka C#.

1. Přidejte následující direktivy using do souboru jazyka C#, kde budete používat nastavení:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Následující kód ilustruje příklad přístupu k připojovacímu řetězci. Nahraďte parametr &lt; connectionstringname> zástupný text odpovídající hodnotou.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Přidání vlastního nastavení pro použití v cloudové službě Azure
Vlastní nastavení v konfiguračním souboru služby umožňují přidat název a hodnotu pro řetězec pro konkrétní konfiguraci služby. Toto nastavení můžete použít ke konfiguraci funkce v cloudové službě tak, že si přečtete hodnotu nastavení a tuto hodnotu použijete k řízení logiky ve vašem kódu. Tyto hodnoty konfigurace služby můžete změnit, aniž byste museli znovu sestavit balíček služby nebo když je vaše cloudová služba spuštěná. Váš kód může kontrolovat oznámení při změně nastavení. Viz [RoleEnvironment. měnící se událost](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Můžete přidat, odebrat nebo upravit vlastní nastavení pro konfigurace služby. V případě různých konfigurací služby můžete chtít pro tyto řetězce různé hodnoty.

Při použití jiné hodnoty pro každou konfiguraci služby nemusíte v cloudové službě používat jiné řetězce ani upravovat kód při publikování cloudové služby do Azure. Můžete použít stejný název řetězce v kódu a hodnota se liší v závislosti na konfiguraci služby, kterou jste vybrali při vytváření cloudové služby nebo při jejím publikování.

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Místní nabídka Průzkumník řešení role Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **Settings** (Nastavení).

    ![Karta nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. V seznamu **Konfigurace služby** vyberte konfiguraci služby, kterou chcete aktualizovat.

    ![Seznam konfigurací služby](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Pokud chcete přidat vlastní nastavení, vyberte **Přidat nastavení**.

    ![Přidat vlastní nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po přidání nového nastavení do seznamu aktualizujte řádek v seznamu s potřebnými informacemi.

    ![Nové vlastní nastavení](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Název** – zadejte název nastavení.
    - V rozevíracím seznamu **typ** vyberte **řetězec** .
    - **Hodnota** – zadejte hodnotu nastavení. Můžete buď zadat hodnotu přímo do buňky **hodnoty** , nebo vybrat tři tečky (...) a zadat hodnotu do dialogového okna **Upravit řetězec** .

1. Pokud chcete odstranit vlastní nastavení, vyberte nastavení a pak vyberte **odebrat nastavení**.

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programový přístup k hodnotě vlastního nastavení

Následující kroky ukazují, jak programově přistupovat k vlastnímu nastavení pomocí jazyka C#.

1. Přidejte následující direktivy using do souboru jazyka C#, kde budete používat nastavení:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Následující kód ilustruje příklad přístupu k vlastnímu nastavení. Nahraďte &lt; zástupný symbol nastavení> odpovídající hodnotou.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Správa místního úložiště pro každou instanci role
Do každé instance role můžete přidat úložiště místních systémů souborů. Data uložená v tomto úložišti nejsou přístupná pro jiné instance role, pro které jsou data uložená, nebo jiné role.

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení**rozbalte uzel projektu. V uzlu **role** klikněte pravým tlačítkem na roli, kterou chcete aktualizovat, a v místní nabídce vyberte možnost **vlastnosti**.

    ![Místní nabídka Průzkumník řešení role Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Vyberte kartu **místní úložiště** .

    ![Karta místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. V seznamu **Konfigurace služby** se ujistěte, že je vybraná možnost **všechny konfigurace** , protože nastavení místního úložiště platí pro všechny konfigurace služby. Výsledkem jakékoli jiné hodnoty jsou všechna vstupní pole na stránce, která je zakázána.

    ![Seznam konfigurací služby](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Pokud chcete přidat položku místního úložiště, vyberte **Přidat místní úložiště**.

    ![Přidat místní úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po přidání nové místní položky úložiště do seznamu aktualizujte řádek v seznamu s potřebnými informacemi.

    ![Položka nového místního úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Název** – zadejte název, který chcete použít pro nové místní úložiště.
    - **Velikost (MB)** – zadejte velikost v MB, kterou potřebujete pro nové místní úložiště.
    - **Vyčistit při recyklaci role** – tuto možnost vyberte, pokud chcete data z nového místního úložiště odebrat, když se virtuální počítač role recykluje.

1. Pokud chcete položku místního úložiště odstranit, vyberte ji a pak vyberte **Odebrat místní úložiště**.

1. Z aplikace Visual Studio na panelu nástrojů vyberte **Uložit**.

## <a name="programmatically-accessing-local-storage"></a>Programový přístup k místnímu úložišti

Tato část ukazuje, jak programově přistupovat k místnímu úložišti pomocí jazyka C# pomocí zápisu testovacího textového souboru `MyLocalStorageTest.txt` .

### <a name="write-a-text-file-to-local-storage"></a>Zapsat textový soubor do místního úložiště

Následující kód ukazuje příklad, jak napsat textový soubor do místního úložiště. &lt;Zástupný text LocalStorageName> nahraďte příslušnou hodnotou.

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

### <a name="find-a-file-written-to-local-storage"></a>Vyhledat soubor napsaný do místního úložiště

Chcete-li zobrazit soubor vytvořený kódem v předchozí části, postupujte podle následujících kroků:

1. V oznamovací oblasti systému Windows klikněte pravým tlačítkem myši na ikonu Azure a v místní nabídce vyberte možnost **Zobrazit uživatelské rozhraní emulátoru COMPUTE**.

    ![Zobrazit emulátor služby COMPUTE Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Vyberte webovou roli.

    ![Emulátor služby COMPUTE Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. V nabídce **Microsoft Azure emulátor COMPUTE** vyberte **nástroje**  >  **otevřít místní úložiště**.

    ![Otevřít položku nabídky místního úložiště](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otevření okna Průzkumník Windows zadejte do textového pole **hledání** text 'MyLocalStorageTest.txt' a spusťte hledání výběrem **ENTER** .

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o projektech Azure v aplikaci Visual Studio čtením [konfigurace projektu Azure](vs-azure-tools-configuring-an-azure-project.md). Další informace o schématu cloudové služby najdete v tématu [Přehled schématu](https://msdn.microsoft.com/library/azure/dd179398).
