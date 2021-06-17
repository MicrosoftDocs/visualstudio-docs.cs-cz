---
title: Ladění sharepointové aplikace pomocí IntelliTrace
description: Pomocí nástroje IntelliTrace můžete snadněji ladit a opravovat aplikace SharePointu. Vytvořte a přidejte kód k příjemci funkcí. Otestujte projekt. Shromažďování dat IntelliTrace.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cf7fa6c7255e05c465d6c209db5e9581a49aee64
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112832"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Návod: Ladění sharepointové aplikace pomocí IntelliTrace

Pomocí nástroje IntelliTrace můžete snadněji ladit řešení služby SharePoint. Tradiční ladicí programy vám v současné době poskytují pouze snímek řešení. Pomocí nástroje IntelliTrace však můžete zkontrolovat minulé události, ke kterým došlo ve vašem řešení, a kontext, ve kterém k nim došlo, a přejít na kód.

 Tento návod ukazuje, jak ladit projekt služby SharePoint v Visual Studio pomocí Microsoft Monitoring Agent ke shromažďování dat IntelliTrace z nasazených aplikací. K analýze dat musíte použít Visual Studio Enterprise. Tento projekt zahrnuje přijímač funkcí, který po aktivaci funkce přidá úkol do seznamu úkolů a oznámení do seznamu Oznámení. Když je funkce deaktivovaná, úloha se označí jako dokončená a do seznamu Oznámení se přidá druhé oznámení. Procedura však obsahuje logickou chybu, která brání správnému spuštění projektu. Pomocí IntelliTrace vyhledáte a opravíte chybu.

 **Platí pro:** Informace v tomto tématu se týkají řešení služby SharePoint, která byla vytvořena v Visual Studio.

 Tento návod znázorňuje následující úlohy:

- [Vytvoření přijímače funkcí](#create-a-feature-receiver)

- [Přidání kódu do přijímače funkcí](#add-code-to-the-feature-receiver)

- [Otestování projektu](#test-the-project)

- [Shromažďování dat IntelliTrace pomocí Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Ladění a oprava řešení služby SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Windows a SharePointu.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Vytvoření přijímače funkcí

Nejprve vytvoříte prázdný projekt SharePointu, který má příjemce funkcí.

1. Vytvořte projekt řešení služby SharePoint, který cílí na nainstalovanou verzi SharePointu, a pojmnte ho **IntelliTraceTest**.

     Zobrazí **se Průvodce přizpůsobením služby SharePoint,** ve kterém můžete zadat sharepointový web pro váš projekt i úroveň důvěryhodnosti řešení.

2. Zvolte tlačítko **Nasadit jako řešení** farmy a pak zvolte **tlačítko** Dokončit.

     Nástroj IntelliTrace pracuje pouze s řešeními farmy.

3. V **Průzkumník řešení** otevřete místní nabídku pro uzel **Funkce** a pak zvolte **Přidat funkci.**

     *Zobrazí se feature1.feature.*

4. Otevřete místní nabídku funkce Feature1.feature a pak zvolte **Add Event Receiver** (Přidat příjemce událostí) a přidejte do této funkce modul kódu.

## <a name="add-code-to-the-feature-receiver"></a>Přidání kódu do přijímače funkcí

Dále přidejte kód do dvou metod v příjemci funkcí: a `FeatureActivated` `FeatureDeactivating` . Tyto metody se aktivují při každé aktivaci nebo deaktivaci funkce v SharePointu.

1. Na začátek třídy přidejte následující kód, který deklaruje proměnné určující `Feature1EventReceiver` sharepointový web a podřízený web:

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

Teď, když je kód přidaný do přijímače funkcí a kolektor dat je spuštěný, nasaďte a spusťte řešení SharePointu a otestujte, jestli funguje správně.

> [!IMPORTANT]
> V tomto příkladu je vyvolána chyba v obslužné rutině události FeatureDeactivating. Později v tomto názorném postupu tuto chybu vyhledáte pomocí souboru .iTrace, který kolektor dat vytvořil.

1. Nasaďte řešení do SharePointu a pak otevřete sharepointový web v prohlížeči.

     Funkce se aktivuje automaticky, což způsobí, že příjemce funkce přidá oznámení a úlohu.

2. Zobrazte obsah seznamů Oznámení a Úlohy.

     Seznam Oznámení by měl mít nové oznámení s názvem Aktivovaná **funkce: IntelliTraceTest_Feature1** a seznam Úlohy by měl mít novou úlohu s názvem **Deaktivovat: IntelliTraceTest_Feature1**. Pokud některé z těchto položek chybí, ověřte, jestli je funkce aktivovaná. Pokud není aktivovaný, aktivujte ho.

3. Deaktivujte funkci provedením následujících kroků:

   1. V nabídce **Akce webu** v SharePointu zvolte **Nastavení webu**.

   2. V **části Akce** webu zvolte odkaz Spravovat funkce **webu.**

   3. Vedle **IntelliTraceTest Feature1** zvolte **tlačítko Deaktivovat.**

   4. Na stránce Upozornění zvolte odkaz **Deaktivovat tuto** funkci.

      Obslužná rutina události FeatureDeactivating() vyvolá chybu.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Shromažďování dat IntelliTrace pomocí Microsoft Monitoring Agent

Pokud nainstalujete Microsoft Monitoring Agent systému, na který běží SharePoint, můžete řešení SharePointu ladit pomocí dat, která jsou konkrétnější než obecné informace, které IntelliTrace vrací. Agent pracuje mimo Visual Studio pomocí rutin PowerShellu k zachycení informací o ladění během spuštění řešení SharePointu.

> [!NOTE]
> Informace o konfiguraci v této části jsou specifické pro tento příklad. Další informace o dalších možnostech konfigurace najdete v tématu [Použití samostatného kolektoru IntelliTrace.](../debugger/using-the-intellitrace-stand-alone-collector.md)

1. Na počítači, na který běží SharePoint, nastavte Microsoft Monitoring Agent [a začněte monitorovat řešení](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Deaktivace funkce:

   1. V nabídce **Akce webu** v SharePointu zvolte **Nastavení webu**.

   2. V **části Akce** webu zvolte odkaz Spravovat funkce **webu.**

   3. Vedle **IntelliTraceTest Feature1** zvolte **tlačítko Deaktivovat.**

   4. Na stránce Upozornění zvolte odkaz **Deaktivovat tuto** funkci.

      Dojde k chybě (v tomto případě kvůli chybě vyvolané obslužnou rutinou události FeatureDeactivating().

3. V okně PowerShellu spusťte příkaz [Stop-WebApplicationMonitoring,](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) který vytvoří soubor .iTrace, zastaví monitorování a restartuje řešení služby SharePoint.

     **Stop-WebApplicationMonitoring***"<\<SharePointSite> \\ SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Ladění a oprava řešení SharePointu

Teď můžete zobrazit soubor protokolu IntelliTrace v Visual Studio a najít a opravit chybu v řešení služby SharePoint.

1. Ve složce \IntelliTraceLogs otevřete soubor .iTrace v Visual Studio.

     Zobrazí **se stránka Souhrn nástroje IntelliTrace.** Vzhledem k tomu, že se chyba nezpracovaná, zobrazí se ID korelace (GUID) SharePointu v oblasti neošetřené výjimky **oddílu** Analýza. Pokud chcete **zobrazit zásobník** volání, ve kterém došlo k chybě, zvolte tlačítko Zásobník volání.

2. Zvolte tlačítko **Debug Exception (Výjimka** ladění).

     Pokud se zobrazí výzva, načtěte soubory symbolů. V okně **IntelliTrace** se výjimka zvýrazní jako Vyvolaná: Došlo k závažné chybě.

     V okně IntelliTrace zvolte výjimku a zobrazte kód, který selhal.

3. Opravte chybu otevřením sharepointového řešení a pak buď zakomentujte nebo odeberete příkaz **throw** v horní části procedury FeatureDeactivating().

4. Znovu sestavte řešení v Visual Studio a pak ho znovu nasaďte na SharePoint.

5. Deaktivujte funkci provedením následujících kroků:

    1. V nabídce **Akce webu** v SharePointu zvolte **Nastavení webu**.

    2. V **části Akce** webu zvolte odkaz Spravovat funkce **webu.**

    3. Vedle **IntelliTraceTest Feature1** zvolte **tlačítko Deaktivovat.**

    4. Na stránce Upozornění zvolte odkaz **Deaktivovat tuto** funkci.

6. Otevřete seznam Úloha a ověřte, že hodnota **Stav** úlohy Deaktivovat je Dokončeno a že její **hodnota %** dokončení je 100 %.

     Kód teď funguje správně.

## <a name="see-also"></a>Viz také

- [Ověření a ladění sharepointového kódu](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Návod: Ověření kódu SharePointu pomocí testů jednotek](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
