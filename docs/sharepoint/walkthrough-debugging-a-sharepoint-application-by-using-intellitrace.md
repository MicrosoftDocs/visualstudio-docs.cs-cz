---
title: 'Návod: Ladění aplikace SharePoint s použitím technologie IntelliTrace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59f801c79c8bb19a63064bdac2fe717ee3e3a845
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295577"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Návod: Ladění aplikace SharePoint s použitím technologie IntelliTrace

S použitím technologie IntelliTrace, můžete snadněji ladit řešení služby SharePoint. Tradiční ladicí programy poskytují pouze snímek řešení v tuto chvíli aktuální. Můžete však použít IntelliTrace ke kontrole minulých událostech, ke kterým došlo ve vašem řešení a kontext, ve kterém došlo k chybě a přejde na kód.

 Tento návod ukazuje, jak ladit projekt služby SharePoint 2010 a SharePoint 2013 v sadě Visual Studio shromažďovat IntelliTrace data z nasazených aplikací pomocí agenta Microsoft Monitoring Agent. Pokud chcete analyzovat tato data, musíte použít Visual Studio Enterprise. Tento projekt obsahuje příjemce funkce, která, pokud je funkce aktivovaná, přidá úkol do seznamu úkolů a oznámení seznam oznámení. Při deaktivaci funkce je úkol označený jako dokončený a druhý oznámení se přidá do seznamu oznámení. Postup však obsahuje logické chyby, která brání projektu ve správném spuštění. S použitím technologie IntelliTrace, budete vyhledejte a opravte chybu.

 **Platí pro:** informace v tomto tématu se vztahují na SharePoint 2010 a SharePoint 2013 řešení, které byly vytvořeny v sadě Visual Studio.

 Tento návod znázorňuje následující úlohy:

- [Vytvoření příjemce funkce](#BKMK_CreateReceiver)

- [Přidání kódu do příjemce funkce](#BKMK_AddCode)

- [Testování projektu](#BKMK_Test1)

- [Shromažďování dat IntelliTrace pomocí agenta Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Ladění a opravy řešení SharePoint](#BKMK_DebugSolution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice systému Windows a SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Vytvoření příjemce funkce

Nejprve vytvořte prázdný projekt SharePoint, který má příjemce funkce.

1. Vytvořte projekt řešení služby SharePoint 2010 a SharePoint 2013 a pojmenujte ho **IntelliTraceTest**.

     **Průvodce přizpůsobením SharePoint** se zobrazí, ve kterém můžete zadat web služby SharePoint pro váš projekt a úroveň důvěryhodnosti řešení.

2. Zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko.

     IntelliTrace pracuje pouze řešení farmy.

3. V **Průzkumníka řešení**, otevřete místní nabídku **funkce** uzel a klikněte na tlačítko **přidat funkci**.

     *Feature1.Feature* se zobrazí.

4. Otevřete místní nabídku pro Feature1.feature a klikněte na tlačítko **přidat příjemce událostí** přidat modul kódu k funkci.

## <a name="add-code-to-the-feature-receiver"></a>Přidání kódu do příjemce funkce

V dalším kroku přidejte kód do dvou metod v příjemce funkce: `FeatureActivated` a `FeatureDeactivating`. Tyto metody aktivuje pokaždé, když se funkce aktivuje nebo deaktivuje v Sharepointu, v uvedeném pořadí.

1. V horní části `Feature1EventReceiver` třídy, přidejte následující kód, který deklaruje proměnné, které určují Sharepointový web a podřízené lokality:

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

2. Nahradit `FeatureActivated` metodu s následujícím kódem:

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

3. Nahradit `FeatureDeactivating` metodu s následujícím kódem:

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

Přidání kódu do příjemce funkce a data Collection je spuštěna, nasazení a spuštění řešení služby SharePoint k ověření, zda správně funguje.

> [!IMPORTANT]
> V tomto příkladu dojde k chybě v obslužné rutině události FeatureDeactivating. Dále v tomto názorném postupu vyhledat tuto chybu pomocí souboru .iTrace, který vytvoří kolekce dat.

1. Nasazení řešení služby SharePoint a potom v prohlížeči otevřete web služby SharePoint.

     Tato funkce automaticky aktivuje, což způsobí jeho příjemce funkce přidání oznámení a úlohy.

2. Zobrazení obsahu seznamů oznámení a úkoly.

     Seznam oznámení by měl mít nové oznámení s názvem **funkce aktivováno: IntelliTraceTest_Feature1**, a seznam úkolů musí mít nový úkol, který je pojmenován **deaktivovat funkce: IntelliTraceTest_ Feature1**. Pokud platí některá z těchto položek chybí, ověřte, zda je funkce aktivovaná. Pokud není aktivovaná, aktivujte ji.

3. Deaktivace funkce provedením následujících kroků:

   1. Na **Akce webu** nabídku v Sharepointu, zvolte **nastavení webu**.

   2. V části **Akce webu**, zvolte **spravovat funkce webu** odkaz.

   3. Vedle položky **IntelliTraceTest Feature1**, zvolte **deaktivovat** tlačítko.

   4. Na stránce s varováním, zvolte **deaktivovat tuto funkci** odkaz.

      Obslužná rutina události FeatureDeactivating() vyvolá chybu.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Shromažďování dat IntelliTrace pomocí agenta Microsoft Monitoring Agent

Pokud instalujete agenta Microsoft Monitoring Agent na počítači se systémem SharePoint, můžete ladit řešení služby SharePoint s použitím dat, která jsou podrobnější než obecné informace, které vrátí IntelliTrace. Agent pracuje mimo sadu Visual Studio pomocí rutin prostředí PowerShell k zaznamenání informací ladění při spuštění řešení služby SharePoint.

> [!NOTE]
> Informace o konfiguraci v této části je specifická pro tento příklad. Další informace o dalších možnostech konfigurace naleznete v tématu [použití samostatného kolektoru IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. Na počítači, na kterém běží SharePoint [nastavení agenta Microsoft Monitoring Agent a začít monitorovat vaše řešení](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Deaktivace funkce:

   1. Na **Akce webu** nabídku v Sharepointu, zvolte **nastavení webu**.

   2. V části **Akce webu**, zvolte **spravovat funkce webu** odkaz.

   3. Vedle položky **IntelliTraceTest Feature1**, zvolte **deaktivovat** tlačítko.

   4. Na stránce s varováním, zvolte **deaktivovat tuto funkci** odkaz.

      (V tomto případě z důvodu chyby vyvolané v obslužné rutině události FeatureDeactivating()) dojde k chybě.

3. V okně Powershellu, spusťte [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) příkaz pro vytvoření souboru .iTrace, zastavit monitorování a restartujte řešení služby SharePoint.

     **Stop-WebApplicationMonitoring***"\<SharePointSite >\\< SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>Ladění a opravy řešení SharePoint

Nyní můžete zobrazit soubor protokolu IntelliTrace v sadě Visual Studio můžete najít a opravit chyby v řešení služby SharePoint.

1. Ve složce \IntelliTraceLogs otevřete soubor .iTrace v sadě Visual Studio.

     **IntelliTrace – Souhrn** se zobrazí stránka. Vzhledem k tomu, že chyba nebyla zpracována, ID korelace SharePoint (GUID) se zobrazí v oblasti neošetřená výjimka **analýzy** oddílu. Zvolte **zásobník volání** tlačítko, pokud chcete zobrazit zásobník volání, kde došlo k chybě.

2. Zvolte **ladit výjimku** tlačítko.

     Pokud se zobrazí výzva, načte soubory symbolů. V **IntelliTrace** okno, jako je zvýrazněn výjimku "vyvolání: došlo k závažné chybě!".

     V okně IntelliTrace zvolte výjimku k zobrazení kódu, který selhal.

3. Opravte chybu otevření řešení služby SharePoint a potom buď okomentováním odpovídajícího nebo odebráním **throw** příkazu v horní části FeatureDeactivating() procedury.

4. Znovu sestavte řešení v sadě Visual Studio a následně ho znovu nasadíte do služby SharePoint.

5. Deaktivace funkce provedením následujících kroků:

    1. Na **Akce webu** nabídku v Sharepointu, zvolte **nastavení webu**.

    2. V části **Akce webu**, zvolte **spravovat funkce webu** odkaz.

    3. Vedle položky **IntelliTraceTest Feature1**, zvolte **deaktivovat** tlačítko.

    4. Na stránce s varováním, zvolte **deaktivovat tuto funkci** odkaz.

6. Otevření seznamu úkolů a ověřte, zda **stav** hodnotu deaktivovat úkolu je "dokončeno" a jeho **dokončeno %** hodnota je 100 %.

     Kód bude nyní fungovat správně.

## <a name="see-also"></a>Viz také:

[Ověřte a ladění kódu pro SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[Návod: Ověření kódu pro SharePoint pomocí testů jednotek](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
