---
title: Získávání informací o službě z úložiště nastavení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711377"
---
# <a name="get-service-information-from-the-settings-store"></a>Získat informace o službě z úložiště nastavení
Úložiště nastavení můžete použít k vyhledání všech dostupných služeb nebo k určení, jestli je konkrétní služba nainstalovaná. Musíte znát typ třídy služby.

## <a name="to-list-the-available-services"></a>Seznam dostupných služeb

1. Vytvořte projekt VSIX s názvem `FindServicesExtension` a pak přidejte vlastní příkaz s názvem `FindServicesCommand` . Další informace o tom, jak vytvořit vlastní příkaz, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) .

2. Do *FindServicesCommand.cs*přidejte následující direktivy using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Získejte úložiště nastavení konfigurace a potom vyhledejte podřízenou kolekci s názvem Services. Tato kolekce zahrnuje všechny dostupné služby. V `MenuItemCommand` metodě odeberte existující kód a nahraďte ho následujícím kódem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

5. V experimentální instanci v nabídce **nástroje** klikněte na **vyvolat FindServicesCommand**.

     Mělo by se zobrazit okno se zprávou se seznamem všech služeb.

     Chcete-li ověřit tato nastavení, můžete použít Editor registru.

## <a name="find-a-specific-service"></a>Vyhledání konkrétní služby
 Tuto metodu můžete také použít <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> k určení, zda je nainstalována konkrétní služba. Musíte znát typ třídy služby.

1. V MenuItemCallback projektu, který jste vytvořili v předchozím postupu, vyhledejte v úložišti nastavení konfigurace `Services` kolekci, která obsahuje podřízenou kolekci s názvem GUID služby. V tomto případě budeme hledat službu help.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Sestavte projekt a spusťte ladění.

3. V experimentální instanci v nabídce **nástroje** klikněte na **vyvolat FindServicesCommand**.

     Měla by se zobrazit zpráva, že je **k dispozici služba help text:**  následovaný hodnotou **true** nebo **false**. Chcete-li ověřit toto nastavení, můžete použít Editor registru, jak je znázorněno v předchozích krocích.
