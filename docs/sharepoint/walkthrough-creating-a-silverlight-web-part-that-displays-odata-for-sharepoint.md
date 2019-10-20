---
title: Vytvořit webovou část Silverlight zobrazující OData pro SharePoint
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 859944c51be0abf2e6a326a06a5e4432a69ee4ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655927"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Návod: Vytvoření webové části Silverlight, která zobrazuje OData pro SharePoint
  SharePoint 2010 zpřístupňuje svá data seznamu prostřednictvím protokolu OData. Služba OData je ve službě SharePoint implementovaná službou RESTful Service ListData. svc. Tento návod ukazuje, jak vytvořit webovou část služby SharePoint, která je hostitelem aplikace Silverlight. Aplikace Silverlight zobrazuje informace o seznamu oznámení služby SharePoint pomocí ListData. svc. Další informace najdete v tématu [rozhraní REST SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) a [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Microsoft Windows a SharePointu.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Vytvoření aplikace Silverlight a webové části Silverlight
 Nejprve v aplikaci Visual Studio vytvořte aplikaci Silverlight. Aplikace Silverlight načítá data ze seznamu oznámení služby SharePoint pomocí služby ListData. svc.

> [!NOTE]
> Žádné verze Silverlightu před 4,0 podporují požadovaná rozhraní pro odkazování na data SharePointového seznamu.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Vytvoření aplikace Silverlight a webové části Silverlight

1. Na panelu nabídek vyberte možnost **soubor**  > **Nový**  > **projekt** . zobrazí se dialogové okno **Nový projekt** .

2. Rozbalte uzel **služby SharePoint** pod možností **vizuál C#**  nebo **Visual Basic**a pak vyberte uzel **2010** .

3. V podokně šablony vyberte šablonu **webové části SharePoint 2010 Silverlight** .

4. Do pole **název** zadejte **SLWebPartTest** a poté klikněte na tlačítko **OK** .

    Zobrazí se dialogové okno **Průvodce přizpůsobením SharePointu** .

5. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL pro web SharePoint serveru, na který chcete ladit definici webu, nebo použijte výchozí umístění (http://<em>System Name</em>/).

6. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** vyberte možnost **nasadit jako řešení farmy** .

    Přestože tento příklad používá řešení farmy, projekty webové části technologie Silverlight lze nasadit jako řešení farmy nebo izolovaného prostoru. Další informace o řešeních v izolovaném prostoru a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7. V části **jak chcete přidružit webovou část technologie Silverlight** na stránce **Zadejte informace o konfiguraci Silverlightu** zvolte možnost **vytvořit nový projekt Silverlight a přidružte jej k přepínači webové části** .

8. Změňte **název** na **SLApplication**, nastavte **jazyk** na hodnotu **Visual Basic** nebo **vizuál C#** a pak nastavte **verzi Silverlight** na **Silverlight 4,0**.

9. Klikněte na tlačítko **Dokončit** . Projekty se zobrazí v **Průzkumník řešení**.

     Řešení obsahuje dva projekty: aplikaci Silverlight a webovou část Silverlight. Aplikace Silverlight načte a zobrazí data ze seznamu ze SharePointu a webová část Silverlight je hostitelem aplikace Silverlight, takže ji můžete zobrazit na SharePointu.

## <a name="customize-the-silverlight-application"></a>Přizpůsobení aplikace Silverlight
 Přidejte do aplikace Silverlight prvky Code a design.

#### <a name="to-customize-the-silverlight-application"></a>Přizpůsobení aplikace Silverlight

1. Přidejte odkaz na sestavení do System. Windows. data v aplikaci Silverlight. Další informace naleznete v tématu [Postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

2. V **Průzkumník řešení**otevřete místní nabídku pro **odkazy**a zvolte možnost **Přidat odkaz na službu**.

    > [!NOTE]
    > Pokud používáte Visual Basic, musíte vybrat ikonu **Zobrazit všechny soubory** v horní části **Průzkumník řešení** a zobrazit tak uzel **odkazy** .

3. Do pole Adresa v dialogovém okně **Přidat odkaz na službu** zadejte adresu URL webu služby SharePoint, například **http://MySPSite** , a pak klikněte na tlačítko **Přejít** .

     Když Silverlight vyhledá službu SharePoint OData ListData. svc, nahradí ji úplnou adresou URL služby. V tomto příkladu se http://myserver http://myserver/_vti_bin/ListData.svc.

4. Kliknutím na tlačítko **OK** přidejte odkaz na službu do projektu a použijte výchozí název služby ServiceReference1.

5. Na panelu nabídek vyberte **sestavení** **řešení**sestavení  > .

6. Přidejte do projektu nový zdroj dat na základě služby SharePoint. Chcete-li to provést, na panelu nabídek vyberte možnost **zobrazit**  >  jiné**zdroje dat** > **Windows** .

     V okně **zdroje dat** se zobrazují všechna dostupná data seznamu služby SharePoint, jako jsou například úkoly, oznámení a kalendář.

7. Přidejte data seznamu oznámení do aplikace Silverlight. Můžete přetáhnout "oznámení" z okna **zdroje dat** do návrháře Silverlight.

     Tím se vytvoří ovládací prvek mřížky vázaný na seznam oznámení na webu služby SharePoint.

8. Změňte velikost ovládacího prvku mřížky tak, aby odpovídal stránce Silverlight.

9. V souboru kódu MainPage. XAML (*MainPage.XAML.cs* pro Visual C# nebo *MainPage. XAML. vb* pro Visual Basic) přidejte následující odkazy na obor názvů.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Do horní části třídy přidejte následující deklarace proměnných.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. Nahraďte `UserControl_Loaded` procedurou následujícím způsobem.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     Zástupný symbol *servername* nahraďte názvem vašeho serveru, na kterém běží SharePoint.

12. Přidejte následující proceduru pro zpracování chyb.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Úprava webové části Silverlight
 Chcete-li povolit ladění Silverlight, změňte vlastnost v projektu webové části technologie Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Úprava webové části Silverlight

1. Otevřete místní nabídku projektu webové části Silverlight (**SLWebPartTest**) a pak zvolte možnost **vlastnosti**.

2. V okně **vlastnosti** klikněte na kartu **SharePoint** .

3. Pokud ještě není vybraná, zaškrtněte políčko **Povolit ladění Silverlight (místo ladění skriptu)** .

4. Uložte projekt.

## <a name="test-the-silverlight-web-part"></a>Testování webové části Silverlight
 Otestujte novou webovou část Silverlight v SharePointu, aby se zajistilo, že bude správně zobrazovat data SharePointového seznamu.

#### <a name="to-test-the-silverlight-web-part"></a>Testování webové části Silverlight

1. Klikněte na klávesu **F5** a sestavte a spusťte řešení služby SharePoint.

2. V SharePointu v nabídce **Akce webu** klikněte na možnost **Nová stránka**.

3. V dialogovém okně **Nová stránka** zadejte název, například **Test webové části SL**, a pak klikněte na tlačítko **vytvořit** .

4. V Návrháři stránky na kartě Nástroje pro **Úpravy** vyberte možnost **Vložit**.

5. V pruhu karet vyberte možnost **Webová část**.

6. V poli **kategorie** vyberte **vlastní** složka.

7. V seznamu **webové části** zvolte webovou část Silverlight a potom kliknutím na tlačítko **Přidat** přidejte webovou část do návrháře.

8. Po provedení všech přidaných webových stránek, klikněte na kartu **Stránka** a pak na panelu nástrojů zvolte tlačítko **Uložit & Zavřít** .

     Webová část Silverlight by nyní měla zobrazovat data oznámení z webu služby SharePoint. Ve výchozím nastavení je stránka uložena v seznamu stránek webu na SharePointu.

    > [!NOTE]
    > Při přístupu k datům v programu Silverlight napříč doménami program Silverlight chrání před chybami zabezpečení, které lze použít pro zneužití webových aplikací. Pokud narazíte na problémy při přístupu ke vzdáleným datům v Silverlightu, podívejte se na téma [Vytvoření služby dostupné napříč hranicemi domén](http://go.microsoft.com/fwlink/?LinkId=223276).

## <a name="see-also"></a>Viz také:
- [Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Nasazení, publikování a Upgrade balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
