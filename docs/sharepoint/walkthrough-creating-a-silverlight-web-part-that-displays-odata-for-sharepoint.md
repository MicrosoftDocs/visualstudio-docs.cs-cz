---
title: 'Návod: Vytvoření webové části Silverlight, která zobrazuje data OData pro službu SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67742078cefcd0608d1cff9a5bab609053544392
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296109"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Návod: Vytvoření webové části Silverlight, která zobrazuje data OData pro službu SharePoint
  SharePoint 2010 zveřejňuje data seznamu pomocí protokolu OData. V Sharepointu službu OData je implementováno služba RESTful ListData.svc. Tento návod ukazuje, jak vytvořit webové části služby SharePoint, který je hostitelem aplikace Silverlight. Aplikace programu Silverlight zobrazí informace o seznamu Sharepointu oznámení pomocí ListData.svc. Další informace najdete v tématu [rozhraní REST služby SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) a [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované vydání systému Microsoft Windows a SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Vytvoření aplikace Silverlight a webové části Silverlight
 Nejprve vytvořte aplikaci Silverlight v sadě Visual Studio. Silverlight aplikace načte data ze seznamu Sharepointu oznámení pomocí služby ListData.svc.  
  
> [!NOTE]  
>  Žádné verze Silverlight před 4.0 podporují požadovaná rozhraní pro odkazování na dat seznamu služby SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>K vytvoření aplikace Silverlight a webové části Silverlight
  
1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt** dialogové okno.  
  
2. Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
3. V podokně šablony vyberte **webové části služby SharePoint 2010 Silverlight** šablony.  
  
4. V **název** zadejte **SLWebPartTest** a klikněte na tlačítko **OK** tlačítko.  
  
    **Průvodce přizpůsobením SharePoint** zobrazí se dialogové okno.  
  
5. Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte adresu URL webu služby SharePoint server, ve kterém chcete ladit definice webu nebo použijte výchozí umístění (http://<em>systémový název</em>/) .  
  
6. V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** zvolte **nasadit jako řešení farmy** přepínač.  
  
    Přestože tento příklad používá řešení farmy, projekty webové části technologie Silverlight můžete nasadit jako farmy nebo řešení v izolovaném prostoru. Další informace o řešení v izolovaném prostoru a řešení farmy najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
7. V **jak chcete přidružit webovou část Silverlight** část **zadejte informace o konfiguraci Silverlight** zvolte **vytvořením nového projektu technologie Silverlight a přidružit webovou část** přepínač.  
  
8. Změnit **název** k **SLApplication**, nastavte **jazyk** buď **jazyka Visual Basic** nebo **Visual C#**, a pak nastavte **verze Silverlight** k **Silverlight 4.0**.  
  
9. Zvolte **Dokončit** tlačítko. Projekty, které se zobrazí v **Průzkumníka řešení**.  
  
     Řešení obsahuje dva projekty: aplikace Silverlight a webové části Silverlight. Aplikace programu Silverlight načte a zobrazí seznam dat ze služby SharePoint a webové části Silverlight je hostitelem aplikace Silverlight, můžete podívat v Sharepointu.  
  
## <a name="customize-the-silverlight-application"></a>Přizpůsobení aplikace Silverlight
 Přidejte kód a návrh prvků do aplikace Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Chcete-li přizpůsobit aplikaci Silverlight
  
1.  Přidáte odkaz na sestavení do System.Windows.Data v aplikaci Silverlight. Další informace najdete v tématu [postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku pro **odkazy**a klikněte na tlačítko **přidat odkaz na službu**.  
  
    > [!NOTE]  
    >  Pokud používáte jazyk Visual Basic, je třeba zvolit **zobrazit všechny soubory** ikonu v horní části **Průzkumníka řešení** zobrazíte **odkazy** uzlu.  
  
3.  V poli Adresa **přidat odkaz na službu** dialogového okna zadejte adresu URL Sharepointového webu, jako například **http://MySPSite**a klikněte na tlačítko **Přejít** tlačítko.  
  
     Když Silverlight vyhledá službu SharePoint OData ListData.svc, nahradí adresu s adresou URL kompletní. V tomto příkladu http://myserver stane http://myserver/_vti_bin/ListData.svc.  
  
4.  Zvolte **OK** tlačítko Přidat odkaz na službu do projektu a použijte výchozí název služby ServiceReference1.  
  
5.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
6.  Přidáte nový zdroj dat do projektu založeného na službě SharePoint. Chcete-li to provést na řádku nabídek, zvolte **zobrazení** > **ostatní Windows** > **zdroje dat**.  
  
     **Zdroje dat** okno zobrazuje všechny dostupné dat seznamu služby SharePoint, jako je například úlohy, oznámení a kalendář.  
  
7.  Přidání dat seznam oznámení do aplikace Silverlight. "Oznámení" můžete přetáhnout z **zdroje dat** okna do návrháře Silverlightu.  
  
     Tím se vytvoří ovládací prvek mřížky vázán na seznam oznámení webu služby SharePoint.  
  
8.  Změnit velikost ovládacího prvku mřížky k vešel na stránku technologie Silverlight.  
  
9. V souboru MainPage.xaml kódu (*MainPage.xaml.cs* pro jazyk Visual C# nebo *MainPage.xaml.vb* v jazyce Visual Basic), přidejte následující odkazy na obor názvů.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Přidejte následující deklarace proměnných v horní části třídy.  
  
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
   
11. Nahradit `UserControl_Loaded` pomocí následujícího postupu.  
  
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
     Nezapomeňte nahradit *ServerName* zástupný symbol s názvem serveru, na němž je spuštěna služba SharePoint.  
  
12. Přidejte následující postup zpracování chyb.  
  
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
       
## <a name="modify-the-silverlight-web-part"></a>Upravit webovou část Silverlight
 Změňte vlastnost v projektu webové části Silverlight pro povolení ladění Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Upravit webovou část Silverlight  
  
1.  Otevřete místní nabídku pro projekt webové části Silverlight (**SLWebPartTest**) a klikněte na tlačítko **vlastnosti**.  
  
2.  V **vlastnosti** okna, vyberte **SharePoint** kartu.  
  
3.  Pokud ještě není vybraná, vyberte **povolit Silverlight ladění (místo ladění skripty)** zaškrtávací políčko.  
  
4.  Uložte projekt.  
  
## <a name="test-the-silverlight-web-part"></a>Testování webové části technologie Silverlight
 Otestujte novou webovou část Silverlight na Sharepointu a ujistěte se, že se data seznamu služby SharePoint zobrazí správně.  
  
#### <a name="to-test-the-silverlight-web-part"></a>K otestování webové části technologie Silverlight  
  
1.  Zvolte **F5** klíč k sestavení a spuštění řešení služby SharePoint.  
  
2.  V Sharepointu na **Akce webu** nabídce zvolte **nová stránka**.  
  
3.  V **nová stránka** dialogové okno, zadejte název, jako například **testu části webu SL**a klikněte na tlačítko **vytvořit** tlačítko.  
  
4.  V návrháři stránky na **nástroje pro úpravu** kartě **vložit**.  
  
5.  V pruhu karet, zvolte **webové části**.  
  
6.  V **kategorie** zvolte **vlastní** složky.  
  
7.  V **webových částí** seznamu, zvolte webové části Silverlight a klikněte na tlačítko **přidat** tlačítko pro přidání webové části do návrháře.  
  
8.  Po provedení všechny nové funkce do webové stránky, který chcete, zvolte **stránky** kartu a klikněte na tlačítko **uložit a zavřít** tlačítko na panelu nástrojů.  
  
     Webové části Silverlight by měl nyní zobrazování oznámení data z webu služby SharePoint. Ve výchozím nastavení na stránce uložený v seznamu stránky webu služby SharePoint.  
  
    > [!NOTE]  
    >  Při přístupu k datům v programu Silverlight napříč doménami, Silverlight chrání před chybami zabezpečení, které je možné zneužít ohrožená místa webových aplikací. Pokud narazíte na potíže při přístupu ke vzdáleným datům v programu Silverlight, přečtěte si téma [zpřístupnění služby k dispozici napříč hranicemi domén](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Viz také:
 [Vytvoření webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Nasazení, publikování a upgrade balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
