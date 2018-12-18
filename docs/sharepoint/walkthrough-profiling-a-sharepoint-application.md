---
title: 'Návod: Profilace aplikace SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5db5e9408a64df80311667267561ee69234fd7d5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852742"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Návod: Profilovat aplikaci služby SharePoint
  Tento návod ukazuje, jak pomocí nástrojů pro profilaci v sadě Visual Studio za účelem optimalizace výkonu aplikace SharePoint. Ukázková aplikace je příjemce událostí funkce Sharepointu, který obsahuje nečinné smyčky, která snižuje výkon příjemce událostí funkce. Profiler sady Visual Studio umožňuje vyhledat a odstranit nejdražší (nejpomalejší provádění) součást projektu, označované také jako *kritickou cestu*.  
  
 Tento návod demonstruje následující úkoly:  
  
- [Přidání funkcí a příjemce událostí funkce](#BKMK_AddFtrandFtrEvntReceiver).  
  
- [Konfigurace a nasazení aplikace služby SharePoint](#BKMK_ConfigSharePointApp).  
  
- [Spuštění aplikace SharePoint](#BKMK_RunSPApp).  
  
- [Zobrazení a interpretace výsledků profilace](#BKMK_ViewResults).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované vydání systému Microsoft Windows a SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-sharepoint-project"></a>Vytvoření projektu služby SharePoint
 Nejprve vytvořte projekt služby SharePoint.  
  
#### <a name="to-create-a-sharepoint-project"></a>Vytvoření projektu služby SharePoint  
  
1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt** dialogové okno.  
  
2. Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
3. V podokně šablony vyberte **projektu služby SharePoint 2010** šablony.  
  
4. V **název** zadejte **ProfileTest**a klikněte na tlačítko **OK** tlačítko.  
  
    **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
5. Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte adresu URL webu služby SharePoint server, ve kterém chcete ladit definice webu nebo použijte výchozí umístění (http://<em>systémový název</em>/) .  
  
6. V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** zvolte **nasadit jako řešení farmy** přepínač.  
  
    V současné době je možné pouze řešení farmy profilu. Další informace o řešení v izolovaném prostoru a řešení farmy najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Zvolte **Dokončit** tlačítko. Projekt se objeví v **Průzkumníka řešení**.  
  
## <a name="add-a-feature-and-feature-event-receiver"></a>Přidání funkcí a příjemce událostí funkce
 V dalším kroku přidejte funkce do projektu spolu s přijímače událostí pro funkci. Tento příjemce událostí bude obsahovat kód, který má být profilována.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Chcete-li přidat funkci a příjemce událostí funkce  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku **funkce** uzlu, zvolte **přidat funkci**a název ponechte výchozí hodnotu **Feature1**.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku pro **Feature1**a klikněte na tlačítko **přidat příjemce událostí**.  
  
     To přidá soubor kódu na funkci s několik obslužných rutin událostí komentované a otevře soubor pro úpravy.  
  
3.  V třídě příjemce události přidejte následující deklarace proměnných.  
  
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
  
4.  Nahradit `FeatureActivated` procedury s následujícím kódem.  
  
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
  
5.  Přidejte následující následující postup `FeatureActivated`postup.  
  
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
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt (**ProfileTest**) a klikněte na tlačítko **vlastnosti**.  
  
7.  V **vlastnosti** dialogového okna zvolte **SharePoint** kartu.  
  
8.  V **aktivní konfiguraci nasazení** klikněte na položku **bez aktivace**.  
  
     Vyberte tuto konfiguraci nasazení můžete ručně aktivovat funkci později v Sharepointu.  
  
9. Uložte projekt.  
  
## <a name="configure-and-deploy-the-sharepoint-application"></a>Nakonfigurujte a nasaďte aplikace služby SharePoint
 Teď, když je projekt SharePoint připravený, nakonfigurovat a nasadit na server SharePoint.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Ke konfiguraci a nasazení aplikace služby SharePoint  
  
1.  Na **analyzovat** nabídce zvolte **spustit Průvodce výkonem**.  
  
2.  Na stránce jeden **Průvodce výkonem**, leave – metoda profilování jako **vzorkování procesoru** a zvolte **Další** tlačítko.  
  
     Jiných metod profilace je možné v rozšířené profilace situacích. Další informace najdete v tématu [metody kolekce výkonu Principy](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  Na stránce dvě **Průvodce výkonem**, ponechat cíl profilu jako **ProfileTest** a zvolte **Další** tlačítko.  
  
     Pokud řešení obsahuje více projektů, zobrazí se v tomto seznamu.  
  
4.  Na stránce tři **Průvodce výkonem**, zrušte zaškrtnutí políčka **povolit profilaci interakce vrstev** zaškrtněte políčko a klikněte na tlačítko **Další** tlačítko.  
  
     Profilování interakce vrstvy (TIP) funkce je užitečná pro měření výkonu aplikace tento dotazování databází, a pro zobrazují počet, kolikrát se žádá na webové stránce. Protože tato data se nevyžaduje v tomto příkladu, nebude jsme tuto funkci povolit.  
  
5.  Na stránce čtyř **Průvodce výkonem**, nechat **spustit profilaci po dokončení průvodce** zaškrtnuté políčko a klikněte na tlačítko **Dokončit** tlačítko.  
  
     Průvodce umožňuje profilace aplikací na serveru, zobrazí **prohlížeč výkonu** okna a pak sestavení, nasadí a spustí aplikaci služby SharePoint.  
  
## <a name="run-the-sharepoint-application"></a>Spuštění aplikace SharePoint
 Aktivovat funkci v Sharepointu, aktivuje `FeatureActivation` události kód ke spuštění.  
  
#### <a name="to-run-the-sharepoint-application"></a>Ke spuštění aplikace SharePoint  
  
1.  V Sharepointu, otevřete **Akce webu** nabídky a klikněte na tlačítko **nastavení webu**.  
  
2.  V **Akce webu** klikněte na položku **spravovat funkce webu** odkaz.  
  
3.  V **funkce** klikněte na položku **aktivovat** vedle **ProfileTest Feature1**.  
  
     Se pozastavení, pokud to provedete, protože nečinné smyčky volána `FeatureActivated` funkce.  
  
4.  Na **Snadné spuštění** vyberte možnosti **uvádí** a pak v **uvádí** klikněte na položku **oznámení**.  
  
     Všimněte si, že nové oznámení byla přidána do seznamu s informacemi o tom, že se aktivoval funkci.  
  
5.  Zavřete webu služby SharePoint.  
  
     Po ukončení služby SharePoint, profiler vytvoří a zobrazí ukázková sestava profilace a uloží ho jako soubor .vsp **ProfileTest** složky projektu.  
  
## <a name="view-and-interpret-the-profile-results"></a>Zobrazení a interpretace výsledků profilu
 Teď, když máte spouštění a profilované aplikace služby SharePoint, prohlédněte si výsledky testu.  
  
#### <a name="to-view-and-interpret-the-profile-results"></a>K zobrazení a interpretace výsledků profilu
  
1.  V **funkce provádějící nejvíce individuální práce** části ukázkové sestavy profilování, Všimněte si, že `TimeCounter` je v horní části seznamu.  
  
     Toto umístění znamená, že `TimeCounter` byla jedna z funkcí s nejvyšší počet vzorků, to znamená, je jedním z největších kritické body výkonu v aplikaci. Tato situace není překvapení, ale protože je úmyslně navržený tak pro demonstrační účely.  
  
2.  V **funkce provádějící nejvíce individuální práce** zvolte `ProcessRequest` odkazu zobrazíte rozdělení nákladů pro `ProcessRequest` funkce.  
  
     V **volat funkce** části `ProcessRequest`, Všimněte si, že **FeatureActiviated** funkce je uveden jako nejdražší MS DTC volal funkci.  
  
3.  V **volat funkce** zvolte **FeatureActivated** tlačítko.  
  
     V **volat funkce** části **FeatureActivated**, `TimeCounter` funkce je uveden jako nejdražší MS DTC volal funkci. V **zobrazení kódu funkce** podokno, zvýrazněný kód (`TimeCounter`) aktivního bodu a hlásit, které vyžadují opravu.  
  
4.  Zavřete sestava profilace vzorku.  
  
     Chcete-li zobrazit sestavu kdykoli znovu, otevřete soubor .vsp ve **prohlížeč výkonu** okna.  
  
## <a name="fix-the-code-and-reprofile-the-application"></a>Opravit kód a reprofile aplikace
 Teď, když byla zjištěna hotspot funkce v aplikaci SharePoint, opravte ji.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Chcete-li opravit kód a reprofile aplikace  
  
1.  V kódu příjemce událostí funkce, okomentujte `TimeCounter` volání metody `FeatureActivated` tak, aby volána.  
  
2.  Uložte projekt.  
  
3.  V **prohlížeč výkonu**, otevřete složku cíle a klikněte na tlačítko **ProfileTest** uzlu.  
  
4.  Na **prohlížeč výkonu** nástrojů v **akce** , vyberte **spustit profilování** tlačítko.  
  
     Pokud chcete změnit vlastnosti profilování před reprofiling aplikaci, zvolte **spustit Průvodce výkonem** tlačítko místo.  
  
5.  Postupujte podle pokynů **spuštění aplikace SharePoint** části dříve v tomto tématu.  
  
     Funkce by měla aktivovat mnohem rychleji teď, když volání nečinné smyčky se odstranilo. Sestava profilace vzorku by tyto změny projeví.  
  
## <a name="see-also"></a>Viz také:
 [Prohlížeč výkonu](/visualstudio/profiling/performance-explorer)   
 [Přehled výkonnostní relace](/visualstudio/profiling/performance-session-overview)   
 [Průvodce začátečníka profilací výkonu](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Vyhledat problémová místa aplikace pomocí sady Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
