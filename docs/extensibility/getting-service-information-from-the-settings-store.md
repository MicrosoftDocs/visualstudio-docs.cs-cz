---
title: Získání informací o službě z úložiště | Microsoft Docs
description: Naučte se používat úložiště nastavení k vyhledání všech dostupných služeb nebo k určení, jestli je konkrétní služba nainstalovaná.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb014803945ea88cd6c2c27eee8c120059014a18
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900639"
---
# <a name="get-service-information-from-the-settings-store"></a>Získání informací o službě z úložiště nastavení
Úložiště nastavení můžete použít k vyhledání všech dostupných služeb nebo k určení, jestli je konkrétní služba nainstalovaná. Musíte znát typ třídy služby.

## <a name="to-list-the-available-services"></a>Zobrazení seznamu dostupných služeb

1. Vytvořte projekt VSIX s názvem `FindServicesExtension` a pak přidejte vlastní příkaz s názvem `FindServicesCommand` . Další informace o vytvoření vlastního příkazu najdete v tématu Vytvoření [rozšíření pomocí příkazu nabídky.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Do *souboru FindServicesCommand.cs* přidejte následující direktivy using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Získejte úložiště nastavení konfigurace a pak vyhledejte podskupinou Services. Tato kolekce zahrnuje všechny dostupné služby. V `MenuItemCommand` metodě odeberte existující kód a nahraďte ho následujícím kódem:

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

4. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.

5. V experimentální instanci v nabídce Nástroje **klikněte** na **Vyvolat FindServicesCommand.**

     Mělo by se zobrazit okno se zprávou se seznamem všech služeb.

     K ověření těchto nastavení můžete použít editor registru.

## <a name="find-a-specific-service"></a>Vyhledání konkrétní služby
 Můžete také použít <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodu k určení, zda je konkrétní služba nainstalována. Musíte znát typ třídy služby.

1. V nabídce MenuItemCallback projektu, který jste vytvořili v předchozím postupu, vyhledejte v obchodě nastavení konfigurace kolekci, která má podřízenou kolekci s názvem `Services` podle identifikátoru GUID služby. V tomto případě budeme hledat službu nápovědy.

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

3. V experimentální instanci v nabídce Nástroje **klikněte** na **Vyvolat FindServicesCommand.**

     Měla by se zobrazit zpráva s textem **Help Service Available (Služba** nápovědy k dispozici): a true **(Pravda)** nebo **False (Nepravda).** K ověření tohoto nastavení můžete použít editor registru, jak je znázorněno v předchozích krocích.
