---
title: Získávání informací o službě z nastavení Store | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4fee0918c0506fe433377a3063c30be1d8b03f89
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789353"
---
# <a name="getting-service-information-from-the-settings-store"></a>Získávání informací o službě z úložiště nastavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení úložiště můžete použít k vyhledání všech dostupných služeb nebo k určení, zda je nainstalován konkrétní službu. Typ třídy služeb, musíte znát.  
  
### <a name="to-list-the-available-services"></a>Seznam dostupných služeb  
  
1.  Vytvořte projekt VSIX s názvem FindServicesExtension a pak přidejte vlastní příkaz s názvem FindServicesCommand. Další informace o tom, jak vytvořit vlastní příkaz najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  V souboru FindServicesCommand.cs, přidejte následující příkazy using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Získat úložiště nastavení konfigurace a pak najít podřízenou kolekci s názvem služby. Tato kolekce obsahuje všechny dostupné služby. V metodě MenuItemCommand odeberte existující kód a nahraďte ji následujícím kódem:  
  
    ```  
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
  
4.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
5.  V experimentální instanci na **nástroje** nabídky, klikněte na tlačítko **vyvolat FindServicesCommand**.  
  
     Měli byste vidět okno se zprávou výpis všech služeb.  
  
     Pokud chcete ověřit nastavení, můžete použít editor registru.  
  
## <a name="finding-a-specific-service"></a>Vyhledání konkrétní služby  
 Můžete také použít <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodou ke zjištění, zda je nainstalován konkrétní službu. Typ třídy služeb, musíte znát.  
  
1.  V MenuItemCallback projektu, kterou jste vytvořili v předchozím postupu, vyhledejte v obchodě nastavení konfigurace `Services` kolekce, která obsahuje podřízenou složku s názvem podle identifikátoru GUID služby. Podíváme se v tomto případě pro službu nápovědy.  
  
    ```  
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
  
2.  Sestavte projekt a spusťte ladění.  
  
3.  V experimentální instanci na **nástroje** nabídky, klikněte na tlačítko **vyvolat FindServicesCommand**.  
  
     Měla zobrazit zpráva s textem **Nápověda služby k dispozici:** následovaný **True** nebo **False**. Pokud chcete ověřit toto nastavení, můžete pomocí Editoru registru, jak je znázorněno v předchozích krocích.

