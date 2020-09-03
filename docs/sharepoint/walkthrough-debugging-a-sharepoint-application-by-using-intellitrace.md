---
title: Ladění aplikace SharePoint pomocí IntelliTrace
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 041a110ee39ae7711756b8d689bdf68ae2368caf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015754"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Návod: ladění aplikace služby SharePoint pomocí IntelliTrace

Pomocí IntelliTrace můžete snadněji ladit řešení služby SharePoint. Tradiční ladicí program poskytuje pouze snímek řešení v aktuálním okamžiku. IntelliTrace však můžete použít ke kontrole minulých událostí, ke kterým došlo ve vašem řešení, a kontextu, ve kterém k nim došlo, a přejít k kódu.

 Tento návod ukazuje, jak ladit projekt SharePoint 2010 nebo SharePoint 2013 v aplikaci Visual Studio pomocí Microsoft Monitoring Agent ke shromáždění dat IntelliTrace z nasazených aplikací. K analýze těchto dat je nutné použít Visual Studio Enterprise. Tento projekt obsahuje přijímač funkcí, který při aktivaci funkce přidá úkol do seznamu úkolů a oznámení do seznamu oznámení. Po deaktivaci této funkce bude úkol označen jako dokončený a do seznamu oznámení se přidá druhé oznámení. Procedura však obsahuje logickou chybu, která brání správnému spuštění projektu. Při použití IntelliTrace vyhledáte a opravíte chybu.

 **Platí pro:** Informace v tomto tématu se vztahují na řešení SharePoint 2010 a SharePoint 2013 vytvořená v aplikaci Visual Studio.

 Tento návod znázorňuje následující úlohy:

- [Vytvoření přijímače funkcí](#create-a-feature-receiver)

- [Přidání kódu do příjemce funkce](#add-code-to-the-feature-receiver)

- [Testování projektu](#test-the-project)

- [Shromažďovat data IntelliTrace pomocí Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Ladění a oprava řešení služby SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Windows a SharePointu.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Vytvoření přijímače funkcí

Nejprve vytvořte prázdný projekt služby SharePoint, který má přijímač funkcí.

1. Vytvořte projekt řešení SharePoint 2010 nebo SharePoint 2013 a pojmenujte ho **IntelliTraceTest**.

     Zobrazí se **Průvodce přizpůsobením SharePointu** , ve kterém můžete zadat web služby SharePoint pro váš projekt a úroveň důvěryhodnosti řešení.

2. Zvolte možnost **nasadit jako řešení farmy** a pak klikněte na tlačítko **Dokončit** .

     IntelliTrace funguje pouze pro řešení farmy.

3. V **Průzkumník řešení**otevřete místní nabídku uzlu **funkce** a zvolte možnost **Přidat funkci**.

     Zobrazí se *Feature1. Feature* .

4. Otevřete místní nabídku pro Feature1. Feature a pak zvolte **Přidat příjemce událostí** a přidejte do funkce modul kódu.

## <a name="add-code-to-the-feature-receiver"></a>Přidání kódu do příjemce funkce

Dále do přijímače funkce přidejte kód do dvou metod: `FeatureActivated` a `FeatureDeactivating` . Tyto metody se aktivují pokaždé, když se aktivuje nebo deaktivuje funkce služby SharePoint v uvedeném pořadí.

1. V horní části `Feature1EventReceiver` třídy přidejte následující kód, který deklaruje proměnné, které určují web služby SharePoint a podřízený web:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Nahraďte metodu `FeatureActivated` následujícím kódem:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Nahraďte metodu `FeatureDeactivating` následujícím kódem:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Testování projektu

Teď, když je kód přidaný do přijímače funkcí a kolekce dat je spuštěný, nasaďte a spusťte řešení SharePoint, abyste otestovali, jestli funguje správně.

> [!IMPORTANT]
> V tomto příkladu je vyvolána chyba v obslužné rutině události FeatureDeactivating. Později v tomto návodu najdete tuto chybu pomocí souboru. iTrace, který vytvořila kolekce dat.

1. Nasaďte řešení do služby SharePoint a pak otevřete web služby SharePoint v prohlížeči.

     Tato funkce se automaticky aktivuje, což způsobí, že příjemce funkce přidá oznámení a úlohu.

2. Zobrazí obsah seznamů oznámení a úkoly.

     Seznam oznámení by měl mít nové oznámení s názvem **aktivovaná funkce: IntelliTraceTest_Feature1**a seznam úkoly by měl mít novou úlohu s názvem **deaktivovat funkci: IntelliTraceTest_Feature1**. Pokud některá z těchto položek chybí, ověřte, zda je funkce aktivována. Pokud není aktivována, aktivujte ji.

3. Deaktivujte funkci provedením následujících kroků:

   1. V nabídce **Akce webu** ve službě SharePoint vyberte možnost **Nastavení webu**.

   2. V části **Akce webu**vyberte odkaz **Spravovat funkce webu** .

   3. Vedle **IntelliTraceTest Feature1**klikněte na tlačítko **deaktivovat** .

   4. Na stránce s upozorněním klikněte na odkaz **deaktivovat tuto funkci** .

      Obslužná rutina události FeatureDeactivating () vyvolá chybu.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Shromažďovat data IntelliTrace pomocí Microsoft Monitoring Agent

Pokud nainstalujete Microsoft Monitoring Agent do systému, na kterém je spuštěna služba SharePoint, můžete ladit řešení služby SharePoint pomocí dat, která jsou konkrétnější než obecné informace, které IntelliTrace vrací. Agent funguje mimo sadu Visual Studio pomocí rutin PowerShellu pro zachycení informací o ladění během běhu řešení služby SharePoint.

> [!NOTE]
> Informace o konfiguraci v této části jsou specifické pro tento příklad. Další informace o dalších možnostech konfigurace najdete v tématu [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. V počítači, na kterém je spuštěna služba SharePoint, [nastavte Microsoft Monitoring Agent a začněte monitorovat vaše řešení](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Deaktivovat funkci:

   1. V nabídce **Akce webu** ve službě SharePoint vyberte možnost **Nastavení webu**.

   2. V části **Akce webu**vyberte odkaz **Spravovat funkce webu** .

   3. Vedle **IntelliTraceTest Feature1**klikněte na tlačítko **deaktivovat** .

   4. Na stránce s upozorněním klikněte na odkaz **deaktivovat tuto funkci** .

      Dojde k chybě (v tomto případě z důvodu chyby vyvolané v obslužné rutině události FeatureDeactivating ()).

3. V okně PowerShellu spusťte příkaz [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) , který vytvoří soubor. iTrace, zastaví monitorování a restartuje řešení služby SharePoint.

     **Stop-WebApplicationMonitoring***" \<SharePointSite> \\<SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Ladění a oprava řešení služby SharePoint

Nyní můžete zobrazit soubor protokolu IntelliTrace v aplikaci Visual Studio a vyhledat a opravit chybu v řešení služby SharePoint.

1. Ve složce \IntelliTraceLogs otevřete soubor. iTrace v aplikaci Visual Studio.

     Zobrazí se stránka **Souhrn IntelliTrace** . Vzhledem k tomu, že chyba nebyla zpracována, zobrazí se ID korelace SharePoint (identifikátor GUID) v neošetřené oblasti výjimek v části **Analýza** . Vyberte tlačítko **zásobník volání** , pokud chcete zobrazit zásobník volání, ve kterém došlo k chybě.

2. Klikněte na tlačítko **výjimka ladění** .

     Pokud se zobrazí výzva, načtěte soubory symbolů. V okně **IntelliTrace** je výjimka zvýrazněna jako "vyvolaná: došlo k závažné chybě!".

     V okně IntelliTrace vyberte výjimku pro zobrazení kódu, který selhal.

3. Opravte chybu tak, že otevřete řešení SharePoint a potom buď Odkomentujte, nebo odeberte příkaz **throw** v horní části postupu FeatureDeactivating ().

4. Znovu sestavte řešení v aplikaci Visual Studio a potom ho znovu nasaďte do SharePointu.

5. Deaktivujte funkci provedením následujících kroků:

    1. V nabídce **Akce webu** ve službě SharePoint vyberte možnost **Nastavení webu**.

    2. V části **Akce webu**vyberte odkaz **Spravovat funkce webu** .

    3. Vedle **IntelliTraceTest Feature1**klikněte na tlačítko **deaktivovat** .

    4. Na stránce s upozorněním klikněte na odkaz **deaktivovat tuto funkci** .

6. Otevřete seznam úkolů a ověřte, zda je hodnota **stav** úlohy deaktivace dokončená a zda je její hodnota **dokončeno%** 100%.

     Kód teď funguje správně.

## <a name="see-also"></a>Viz také

- [Ověření a ladění kódu pro SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Návod: ověření kódu služby SharePoint pomocí testů jednotek](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))