---
title: 'Návod: Návrh oblasti formuláře Outlooku'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 693261bb6894681b613ad0db2f0b3c116109a782
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813684"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Návod: Návrh oblasti formuláře Outlooku
  Vlastní formulář oblastech rozšířit standardní nebo vlastní formuláře aplikace Microsoft Office Outlook. V tomto návodu bude navrhovat vlastní formulář regionu, který se zobrazí v okně Inspektor kontaktní položky na novou stránku. Tato oblast formuláře zobrazí se mapa s každou adresu, která je uvedena u kontaktu, posíláním informací o adresy na Windows Live místní vyhledávací web. Informace o oblasti formuláře, naleznete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvoření nového projektu doplňku VSTO v Outlooku.  
  
-   Přidání oblasti formuláře do projektu doplňku VSTO.  
  
-   Návrh rozložení oblasti formuláře.  
  
-   Přizpůsobení chování oblasti formuláře.  
  
-   Testuje se oblast formuláře Outlooku.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] nebo [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") video verzi tohoto tématu naleznete v tématu [Video postupy: Návrh oblasti formuláře Outlooku](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook  
 Vytvoření základního projektu doplňku VSTO.  
  
### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Outlook  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvoření projektu doplňku VSTO pro Outlook s názvem **MapItAddIn**.  
  
2.  V **nový projekt** dialogu **vytvořit adresář pro řešení**.  
  
3.  Uložte projekt do libovolného adresáře.  
  
     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Přidání oblasti formuláře do projektu doplňku VSTO pro Outlook  
 Řešení doplňku VSTO pro Outlook může obsahovat jednu nebo více položek oblasti formuláře aplikace Outlook. Přidání položky oblasti formuláře do projektu s použitím **novou oblast formuláře Outlooku** průvodce.  
  
### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Přidání oblasti formuláře do projektu doplňku VSTO pro Outlook  
  
1.  V **Průzkumníka řešení**, vyberte **MapItAddIn** projektu.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogu **oblast formuláře Outlooku**, pojmenujte soubor **MapIt**a potom klikněte na tlačítko **přidat**.  
  
     **Oblasti formuláře NewOutlook** spustí se průvodce.  
  
4.  Na **vyberte způsob vytvoření oblasti formuláře** klikněte na **navrhnout novou oblast formuláře**a potom klikněte na tlačítko **Další**.  
  
5.  Na **výběr typu oblasti formuláře chcete vytvořit** klikněte na **samostatné**a potom klikněte na tlačítko **Další**.  
  
     A *samostatné* oblasti formuláře přidá novou stránku do formuláře aplikace Outlook. Další informace o oblasti formuláře typu naleznete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
6.  Na **zadání popisného textu a výběr předvoleb zobrazení** zadejte **mapy ho** v **název** pole.  
  
     Tento název se zobrazí na pásu karet v okně Inspektor při otevření položky kontaktu.  
  
7.  Vyberte **kontroly, které jsou v režimu vytváření** a **kontroly, které jsou v režimu čtení**a potom klikněte na tlačítko **Další**.  
  
8.  Na **identifikování tříd zpráv, které budou zobrazovat tuto oblast formuláře** zrušte **e-mailovou zprávu**vyberte **kontakt**a potom klikněte na tlačítko **Dokončit**.  
  
     A *MapIt.cs* nebo *MapIt.vb* přidá soubor do projektu.  
  
## <a name="design-the-layout-of-the-form-region"></a>Návrh rozložení oblasti formuláře  
 Vývoj oblastí formulářů vizuálně pomocí *návrhářem oblasti formuláře*. Spravované ovládací prvky můžete přetáhnout na plochu návrháře oblasti formuláře. Použít návrháře a **vlastnosti** okno pro úpravu ovládací prvek rozložení a vzhled.  
  
### <a name="to-design-the-layout-of-the-form-region"></a>Návrh rozložení oblasti formuláře  
  
1.  V **Průzkumníka řešení**, rozbalte **MapItAddIn** projektu a potom dvakrát klikněte na panel *MapIt.cs* nebo *MapIt.vb* otevřete oblast formuláře Návrhář.  
  
2.  Pravým tlačítkem myši klepněte Návrhář a potom klikněte na **vlastnosti**.  
  
3.  V **vlastnosti** okno, nastavte **velikost** k **664, 469**.  
  
     Tím se zajistí, že bude dostatečně velký pro zobrazení mapě oblasti formuláře.  
  
4.  Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.  
  
5.  Z **běžné ovládací prvky** kartě **nástrojů**, přidejte **WebBrowser** na oblast formuláře.  
  
     **WebBrowser** zobrazí mapu každou adresu, která je uvedena u kontaktu.  
  
## <a name="customize-the-behavior-of-the-form-region"></a>Přizpůsobení chování oblasti formuláře  
 Přidáte kód do obslužné rutiny událostí oblasti formuláře k úpravám způsobu oblasti formuláře chování za běhu. Pro tuto oblast formuláře kód prozkoumá vlastnosti položky aplikace Outlook a určuje, zda má oblast formuláře mapy ho zobrazit. Pokud se zobrazí oblasti formuláře, kód přejde na Windows Live místní hledání a načte mapy pro každou adresu uvedené v položce kontaktů aplikace Outlook.  
  
### <a name="to-customize-the-behavior-of-the-form-region"></a>Chcete-li přizpůsobit chování oblasti formuláře  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši *MapIt.cs* nebo *MapIt.vb*a potom klikněte na tlačítko **zobrazit kód**.  
  
    *MapIt.cs* nebo *MapIt.vb* otevře v editoru kódu.  
  
2. Rozbalte **objekt pro vytváření oblasti formuláře** oblasti kódu.  
  
    Třída objekt pro vytváření oblasti formuláře s názvem `MapItFactory` je přístupný.  
  
3. Přidejte následující kód, který `MapItFactory_FormRegionInitializing` obslužné rutiny události. Tato obslužná rutina události je volána, když uživatel otevře kontakt. Následující kód určuje, zda kontaktní položka obsahuje adresu. Pokud položka kontaktu neobsahuje adresu, tento kód nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> třídu **true** a oblasti formuláře se nezobrazí. V opačném případě vyvolá doplňku VSTO <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> událostí a zobrazí oblasti formuláře.  
  
    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4. Přidejte následující kód, který <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> obslužné rutiny události. Tento kód provede následující:  
  
   - Zřetězí jednotlivé adresy v položce kontaktu a vytvoří řetězec adresy URL.  
  
   - Volání <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metodu <xref:System.Windows.Forms.WebBrowser> objektu a předá jako parametr řetězec adresy URL.  
  
     Místní vyhledávací web se zobrazí v oblasti formuláře mapy ho a uvede každou adresu v oblasti začátku.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="test-the-outlook-form-region"></a>Testovací oblast formuláře Outlooku  
 Při spuštění projektu sady Visual Studio otevře aplikace Outlook. Kontaktní položku k zobrazení oblasti formuláře mapy ho otevřete. Oblast formuláře mapování se zobrazí jako stránky ve formuláři u každého kontaktu, který obsahuje adresu.  
  
### <a name="to-test-the-map-it-form-region"></a>K otestování oblasti formuláře mapy ho  
  
1.  Stisknutím klávesy **F5** spusťte projekt.  
  
     Otevře se aplikace Outlook.  
  
2.  V aplikaci Outlook na **Domů** klikněte na tlačítko **nové položky**a potom klikněte na tlačítko **kontakt**.  
  
3.  Zadejte kontaktní formulář **Ann Beebe** jako kontakt pojmenujte a pak zadejte následující tři adresy.  
  
    |Typ adresy|Adresa|  
    |------------------|-------------|  
    |**firmy**|**Svatý hlavní 4567 Buffalo, NY**|  
    |**Domovská stránka**|**Svatý severní 1234 Buffalo, NY**|  
    |**Jiné**|**3456 hlavní St. Seattle, WA**|  
  
4.  Uložte a zavřete položky kontaktu.  
  
5.  Znovu otevřít **Ann Beebe** kontakt.  
  
6.  V **zobrazit** skupiny pásu karet položky, klikněte na tlačítko **mapy ho** oblasti formuláře mapy ho otevřete.  
  
     Oblast formuláře mapování se zobrazí se místní vyhledávací web. **Obchodní**, **Domů**, a **jiných** adresy se zobrazí v oblasti začátku. V oblasti začátku vyberte adresu, kterou chcete namapovat.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak přizpůsobit uživatelské rozhraní aplikace Outlook z těchto témat:  
  
-   Další informace o tom, jak přizpůsobit na pásu karet položky Outlooku, naleznete v tématu [přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Návod: Importujte oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Postupy: zabránění zobrazení oblasti formuláře Outlooku](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  