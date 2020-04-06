---
title: Získání informací o službě z úložiště nastavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711377"
---
# <a name="get-service-information-from-the-settings-store"></a>Získání informací o službě z úložiště nastavení
Úložiště nastavení můžete použít k vyhledání všech dostupných služeb nebo k určení, zda je nainstalována určitá služba. Musíte znát typ třídy služeb.

## <a name="to-list-the-available-services"></a>Chcete-li uvést dostupné služby

1. Vytvořte projekt VSIX s názvem `FindServicesExtension` a `FindServicesCommand`přidejte vlastní příkaz s názvem . Další informace o vytvoření vlastního příkazu najdete [v tématu Vytvoření rozšíření pomocí příkazu nabídky.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. V *FindServicesCommand.cs*přidejte následující příkazy:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Získejte úložiště nastavení konfigurace a vyhledejte podkolekci s názvem Služby. Tato kolekce obsahuje všechny dostupné služby. V `MenuItemCommand` metodě odeberte existující kód a nahraďte jej následujícím:

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

4. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

5. V experimentální instanci klepněte v nabídce **Nástroje** na **příkaz Invoke FindServicesCommand**.

     Měli byste vidět okno se zprávou, ve které jsou uvedeny všechny služby.

     Chcete-li ověřit tato nastavení, můžete použít editor registru.

## <a name="find-a-specific-service"></a>Vyhledání konkrétní služby
 Tuto metodu <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> můžete také použít k určení, zda je nainstalována určitá služba. Musíte znát typ třídy služeb.

1. V MenuItemCallback projektu, který jste vytvořili v předchozím postupu, `Services` vyhledejte v úložišti nastavení konfigurace kolekci, která má podkolekci pojmenovanou identifikátorem GUID služby. V takovém případě se podíváme na službu nápovědy.

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

2. Sestavení projektu a začít ladění.

3. V experimentální instanci klepněte v nabídce **Nástroje** na **příkaz Invoke FindServicesCommand**.

     Měla by se zobrazit zpráva s textovou **službou Nápověda k dispozici:** následovaná **hodnotou True** nebo **False**. Chcete-li toto nastavení ověřit, můžete použít editor registru, jak je znázorněno v předchozích krocích.
