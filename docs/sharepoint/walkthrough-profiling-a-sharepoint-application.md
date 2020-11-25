---
title: 'Návod: profilace aplikace SharePoint | Microsoft Docs'
description: V tomto návodu použijte nástroje pro profilaci v aplikaci Visual Studio k optimalizaci výkonu aplikace SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66e19f7744a56d147fb0760c6f20254ea4308603
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970111"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Návod: profilování aplikace SharePoint
  Tento návod ukazuje, jak používat nástroje pro profilaci v aplikaci Visual Studio k optimalizaci výkonu aplikace služby SharePoint. Ukázková aplikace je přijímač událostí funkce SharePointu, který obsahuje smyčku nečinnosti, která snižuje výkon přijímače událostí funkce. Profiler sady Visual Studio umožňuje vyhledat a eliminovat nejnákladný (nejpomalejší) část projektu, označovanou také jako *horká cesta*.

 Tento názorný postup ukazuje následující úlohy:

- [Přidejte přijímač událostí funkce a funkce](#add-a-feature-and-feature-event-receiver).

- [Nakonfigurujte a nasaďte aplikaci SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Spusťte aplikaci SharePoint](#run-the-sharepoint-application).

- [Zobrazení a interpretace výsledků profilu](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Microsoft Windows a SharePointu.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Vytvoření projektu služby SharePoint
 Nejprve vytvořte projekt služby SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Vytvoření projektu služby SharePoint

1. Na panelu nabídek vyberte možnost **soubor**  >  **Nový**  >  **projekt** . zobrazí se dialogové okno **Nový projekt** .

2. Rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

3. V podokně šablony vyberte šablonu **projektu SharePoint 2010** .

4. Do pole **název** zadejte **ProfileTest** a poté klikněte na tlačítko **OK** .

    Zobrazí se **Průvodce přizpůsobením SharePointu** .

5. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL pro web SharePoint serveru, na který chcete ladit definici webu, nebo použijte výchozí umístění (http://<em>System Name</em>/).

6. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** vyberte možnost **nasadit jako řešení farmy** .

    V současné době můžete profilovat pouze řešení farmy. Další informace o řešeních v izolovaném prostoru a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7. Klikněte na tlačítko **Dokončit** . Projekt se zobrazí v **Průzkumník řešení**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Přidání funkce a přijímače událostí funkcí
 Dále do projektu přidejte funkci spolu s přijímačem událostí pro funkci. Tento přijímač událostí bude obsahovat kód, který se má profilovat.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Přidání funkce a přijímače událostí funkcí

1. V **Průzkumník řešení** otevřete místní nabídku uzlu **funkce** , vyberte možnost **Přidat funkci** a ponechte název na výchozí hodnotu **Feature1**.

2. V **Průzkumník řešení** otevřete místní nabídku pro **Feature1** a pak zvolte **Přidat přijímač událostí**.

     Tím se do funkce přidá soubor kódu s několika obslužnými rutinami událostí s komentářem a otevře se soubor pro úpravy.

3. Do třídy přijímač událostí přidejte následující deklarace proměnných.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. Nahraďte `FeatureActivated` proceduru následujícím kódem.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
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

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. Následující postup přidejte pod `FeatureActivated` proceduru.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. V **Průzkumník řešení** otevřete místní nabídku pro projekt (**ProfileTest**) a pak zvolte **vlastnosti**.

7. V dialogovém okně **vlastnosti** klikněte na kartu **SharePoint** .

8. V seznamu **Konfigurace aktivního nasazení** vyberte možnost **bez aktivace**.

     Výběr této konfigurace nasazení vám umožní ručně aktivovat funkci později v SharePointu.

9. Uložte projekt.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Konfigurace a nasazení aplikace SharePoint
 Teď, když je projekt SharePoint připravený, nakonfigurujte a nasaďte ho na SharePointový Server.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Konfigurace a nasazení aplikace služby SharePoint

1. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem**.

2. Na stránce jeden z **Průvodce výkonem** ponechte metodu profilování jako **vzorkování procesoru** a klikněte na tlačítko **Další** .

     Další metody profilace lze použít v pokročilejších situacích profilace. Další informace najdete v tématu [principy metod shromažďování výkonu](../profiling/understanding-performance-collection-methods.md).

3. Na druhé straně **Průvodce výkonem** ponechte cíl profilu jako **ProfileTest** a klikněte na tlačítko **Další** .

     Pokud má řešení více projektů, zobrazí se v tomto seznamu.

4. Na stránce tři **Průvodce výkonem** zrušte zaškrtnutí políčka **Povolit Profilování interakce vrstev** a pak klikněte na tlačítko **Další** .

     Funkce profilování interakce vrstev (TIP) je užitečná pro měření výkonu aplikací, které dotazují databáze a které vám ukáže, kolikrát se webová stránka požaduje. Vzhledem k tomu, že tato data nejsou v tomto příkladu vyžadována, tuto funkci Nepovolíme.

5. Na stránce čtyři **Průvodce výkonem** ponechte zaškrtnuté políčko **Spustit profilaci po dokončení průvodce** a pak klikněte na tlačítko **Dokončit** .

     Průvodce povolí profilaci aplikace na serveru, zobrazí okno **prohlížeč výkonu** a poté sestaví, nasadí a spustí aplikaci služby SharePoint.

## <a name="run-the-sharepoint-application"></a>Spuštění aplikace SharePoint
 Aktivujte funkci ve službě SharePoint, která aktivuje `FeatureActivation` spuštění kódu události.

### <a name="to-run-the-sharepoint-application"></a>Spuštění aplikace SharePoint

1. V SharePointu otevřete nabídku **Akce webu** a zvolte možnost **Nastavení webu**.

2. V seznamu **Akce webu** vyberte odkaz **Spravovat funkce webu** .

3. V seznamu **funkce** klikněte na tlačítko **aktivovat** vedle položky **ProfileTest Feature1**.

     Pokud to uděláte, dojde k pozastavení v důsledku volání nečinné smyčky ve `FeatureActivated` funkci.

4. Na panelu **Snadné spuštění** zvolte **seznamy** a potom v seznamu **seznamy** zvolte možnost **oznámení**.

     Všimněte si, že do seznamu bylo přidáno nové oznámení s oznámením, že byla funkce aktivována.

5. Zavřete web služby SharePoint.

     Po zavření služby SharePoint Profiler vytvoří a zobrazí ukázkovou sestavu profilace a uloží ji jako soubor. vsp ve složce projektu **ProfileTest** .

## <a name="view-and-interpret-the-profile-results"></a>Zobrazení a interpretace výsledků profilu
 Nyní, když jste spustili a profilaci aplikace služby SharePoint, zobrazte výsledky testu.

### <a name="to-view-and-interpret-the-profile-results"></a>Zobrazení a interpretace výsledků profilu

1. Ve funkcích, které **provádějí Nejjednotlivější pracovní** část sestavy profilace vzorku, si všimněte, že `TimeCounter` je poblíž horní části seznamu.

     Toto umístění označuje, že `TimeCounter` byla jednou z funkcí s největším počtem vzorků, což znamená, že se jedná o jeden z největších problémů s výkonem v aplikaci. Tato situace se ale Nepřekvapivé, protože byla navržena záměrně pro demonstrační účely.

2. Ve funkcích, které **provádějí většinu individuální práce** , vyberte `ProcessRequest` odkaz pro zobrazení distribuce nákladů pro `ProcessRequest` funkci.

     V oddílu **volané funkce** pro si `ProcessRequest` Všimněte, že funkce **FeatureActiviated** je uvedena jako nejdražší volaná funkce.

3. V části **volané funkce** klikněte na tlačítko **FeatureActivated** .

     V oddílu **volané funkce** pro **FeatureActivated** `TimeCounter` je funkce uvedena jako nejdražší volaná funkce. V podokně **zobrazení kódu funkce** je zvýrazněný kód ( `TimeCounter` ) hotspot a indikuje, kde je nutná oprava.

4. Zavřete sestavu ukázka profilace.

     Chcete-li sestavu kdykoli zobrazit, otevřete soubor. vsp v okně **prohlížeč výkonu** .

## <a name="fix-the-code-and-reprofile-the-application"></a>Oprava kódu a znovu profilování aplikace
 Nyní je funkce HotSpot v aplikaci SharePoint identifikována a opravena.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Oprava kódu a znovu profilování aplikace

1. V kódu přijímače událostí funkce přihlaste `TimeCounter` k metodě volání metody, `FeatureActivated` abyste zabránili jejímu volání.

2. Uložte projekt.

3. V **prohlížeč výkonu** otevřete složku cíle a pak zvolte uzel **ProfileTest** .

4. Na panelu nástrojů **prohlížeč výkonu** na kartě **Akce** klikněte na tlačítko **Spustit profilaci** .

     Chcete-li změnit některou z vlastností profilace před změnou profilování aplikace, použijte místo toho tlačítko **Průvodce spouštěním výkonu** .

5. Postupujte podle pokynů v části **spuštění aplikace služby SharePoint** , dříve v tomto tématu.

     Tato funkce by se měla aktivovat mnohem rychleji, když se neodstraní volání do nečinné smyčky. Sestava profilace vzorku by se měla odrážet.

## <a name="see-also"></a>Viz také
- [Přehled výkonnostní relace](../profiling/performance-session-overview.md)
- [Příručka pro začátečníky k profilaci výkonu](../profiling/beginners-guide-to-performance-profiling.md)
- [Hledání kritických bodů aplikace pomocí profileru sady Visual Studio](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler)