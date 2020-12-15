---
title: 'Návod: návrh oblasti formuláře aplikace Outlook'
description: Zjistěte, jak můžete navrhnout vlastní oblast formuláře aplikace Microsoft Outlook, která se zobrazí jako nová stránka v okně inspektoru položky kontaktu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e306814512c6cab2d331a26128f22bb94d7dbbf4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524209"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Návod: návrh oblasti formuláře aplikace Outlook
  Vlastní oblasti formuláře rozšíří standardní nebo vlastní systém Microsoft Office Outlook Forms. V tomto návodu navrhnete vlastní oblast formuláře, která se zobrazí jako nová stránka v okně inspektoru položky kontaktu. Tato oblast formuláře zobrazuje mapu každé adresy, která je uvedena u kontaktu, odesláním informací o adrese na web místní vyhledávání na webu Windows Live. Informace o oblastech formuláře najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváří se nový projekt doplňku VSTO pro Outlook.

- Přidání oblasti formuláře do projektu doplňku VSTO.

- Návrh rozložení oblasti formuláře.

- Přizpůsobení chování oblasti formuláře.

- Testování oblasti formuláře aplikace Outlook.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] nebo novější.

  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") Verzi videa tohoto tématu naleznete v části [Video postupy: návrh oblasti formuláře aplikace Outlook](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook
 Nejdřív vytvořte základní projekt doplňku VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvořte projekt doplňku VSTO pro Outlook s názvem **MapItAddIn**.

2. V dialogovém okně **Nový projekt** vyberte **vytvořit adresář pro řešení**.

3. Uložte projekt do libovolného adresáře.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Přidání oblasti formuláře do projektu doplňku VSTO pro Outlook
 Řešení doplňku VSTO pro Outlook může obsahovat jednu nebo více položek oblastí formuláře Outlooku. Přidejte položku oblasti formuláře do projektu pomocí Průvodce vytvořením **nové oblasti formuláře Outlooku** .

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Přidání oblasti formuláře do projektu doplňku VSTO pro Outlook

1. V **Průzkumník řešení** vyberte projekt **MapItAddIn** .

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte možnost **oblast formuláře aplikace Outlook**, pojmenujte soubor **MapIt** a klikněte na tlačítko **Přidat**.

     Spustí se průvodce **oblastí formuláře NewOutlook** .

4. Na stránce **Vyberte, jak chcete vytvořit oblast formuláře** , klikněte na **návrh nové oblasti formuláře** a potom klikněte na tlačítko **Další**.

5. Na stránce **Vyberte typ oblasti formuláře, který chcete vytvořit** klikněte na možnost **samostatné** a potom klikněte na tlačítko **Další**.

     *Samostatná* oblast formuláře přidá novou stránku do formuláře aplikace Outlook. Další informace o typech oblastí formuláře najdete v tématu věnovaném [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

6. **Do pole** **název** zadejte **popisný text pro zadání a vyberte stránku předvolby zobrazení** .

     Tento název se zobrazí na pásu karet okna inspektoru, když je položka kontaktu otevřená.

7. Vyberte **kontrolory, které jsou v režimu psaní** a **kontrolory, které jsou v režimu čtení**, a potom klikněte na tlačítko **Další**.

8. V části **Určete třídy zpráv, které budou zobrazovat tuto stránku oblasti formuláře** , zrušte zaškrtnutí políčka **e-mailová zpráva**, vyberte **kontakt** a pak klikněte na **Dokončit**.

     Do projektu se přidá soubor *MapIt.cs* nebo *MapIt. vb* .

## <a name="design-the-layout-of-the-form-region"></a>Návrh rozložení oblasti formuláře
 Vizuální vývoj oblastí formuláře pomocí *návrháře oblasti formuláře*. Spravované ovládací prvky můžete přetáhnout na plochu návrháře oblasti formuláře. Pro úpravu rozložení a vzhledu ovládacího prvku použijte návrháře a okno **vlastnosti** .

### <a name="to-design-the-layout-of-the-form-region"></a>Návrh rozložení oblasti formuláře

1. V **Průzkumník řešení** rozbalte projekt **MapItAddIn** a dvojitým kliknutím na *MapIt.cs* nebo *MapIt. vb* otevřete návrhář oblasti formuláře.

2. Klikněte pravým tlačítkem na návrháře a pak klikněte na **vlastnosti**.

3. V okně **vlastnosti** nastavte **Velikost** na **664, 469**.

     Tím se zajistí, že oblast formuláře bude dostatečně velká, aby se zobrazila mapa.

4. V nabídce **zobrazení** klikněte na příkaz **Sada nástrojů**.

5. Na kartě **běžné ovládací prvky** **panelu nástrojů** přidejte ovládací prvek **WebBrowser** do oblasti formuláře.

     V **ovládacím prvku WebBrowser** se zobrazí mapa každé adresy, která je uvedena pro daný kontakt.

## <a name="customize-the-behavior-of-the-form-region"></a>Přizpůsobení chování oblasti formuláře
 Přidejte kód do obslužných rutin událostí oblasti formuláře pro přizpůsobení způsobu, jakým se oblast formuláře chová v době běhu. V této oblasti formuláře kód prověřuje vlastnosti položky Outlook a určí, zda se má zobrazit oblast formuláře mapy. Pokud se zobrazí oblast formuláře, kód přejde na místní vyhledávání služby Windows Live a načte mapu každé adresy uvedené v položce kontaktů Outlooku.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Přizpůsobení chování oblasti formuláře

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na *MapIt.cs* nebo *MapIt. vb* a pak klikněte na **Zobrazit kód**.

    V editoru kódu se otevře *MapIt.cs* nebo *MapIt. vb* .

2. Rozbalte oblast kód pro **vytváření oblasti formuláře** .

    Třída factory oblasti formuláře s názvem `MapItFactory` je vystavena.

3. Přidejte následující kód do `MapItFactory_FormRegionInitializing` obslužné rutiny události. Tato obslužná rutina události se volá, když uživatel otevře položku kontaktu. Následující kód určuje, zda položka kontaktu obsahuje adresu. Pokud položka kontaktu neobsahuje adresu, tento kód nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> třídy na **hodnotu true** a oblast formuláře se nezobrazí. V opačném případě doplněk VSTO vyvolá <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> událost a zobrazí oblast formuláře.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Přidejte následující kód do <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> obslužné rutiny události. Tento kód provádí následující úlohy:

   - Zřetězí každou adresu v položce kontaktu a vytvoří řetězec adresy URL.

   - Volá <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metodu <xref:System.Windows.Forms.WebBrowser> objektu a předá řetězec adresy URL jako parametr.

     Místní web hledání se zobrazí v oblasti mapa IT a uvede každou adresu v panelu pro vymazání.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Testování oblasti formuláře aplikace Outlook
 Při spuštění projektu aplikace Visual Studio otevře aplikaci Outlook. Otevřete položku kontaktu pro zobrazení oblasti mapa formuláře. Oblast formuláře mapa IT se zobrazí jako stránka ve formě libovolné položky kontaktu, která obsahuje adresu.

### <a name="to-test-the-map-it-form-region"></a>Otestování oblasti formuláře mapy IT

1. Stisknutím klávesy **F5** spusťte projekt.

     Otevře se Outlook.

2. V Outlooku na kartě **Domů** klikněte na **nové položky** a potom klikněte na **kontakt**.

3. Ve formuláři kontaktu jako jméno kontaktu zadejte **Ann Beebe** a pak zadejte následující tři adresy.

    |Typ adresy|Adresa|
    |------------------|-------------|
    |**Firemní**|**4567 Main St. buvolí, NY**|
    |**Domů**|**1234 Severní St. buvolí, NY**|
    |**Další**|**3456 Main St. Praha, WA**|

4. Uložte a zavřete položku kontaktu.

5. Znovu otevřete položku kontaktu **Ann Beebe** .

    V Outlooku to můžete udělat ve skupině **Najít** tak, že otevřete adresář pro kontakty nebo zadáte Ann Beebe na **Hledat lidi**.

6. Ve skupině **Zobrazit** na pásu karet položky klikněte na tlačítko **mapování** pro otevření oblasti formulář mapy IT.

     Zobrazí se oblast formulář mapy IT a zobrazí se web místní vyhledávání. Adresa pro **firmy**, **Domovská stránka** a **Další** adresy se zobrazí v panelu pro vymazání. V panelu pro poškrábaný vyberte adresu, kterou chcete namapovat.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak přizpůsobit uživatelské rozhraní aplikace Outlook, najdete v těchto tématech:

- Další informace o tom, jak přizpůsobit pás karet položky Outlooku, najdete v tématu [přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Viz také
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
