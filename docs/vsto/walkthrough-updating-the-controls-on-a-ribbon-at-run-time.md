---
title: 'Návod: aktualizace ovládacích prvků na pásu karet v době běhu'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c2e870f028b3337fd162adde881281d7050e142
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298051"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Návod: aktualizace ovládacích prvků na pásu karet v době běhu

Tento návod ukazuje, jak pomocí modelu objektu pásu karet aktualizovat ovládací prvky na pásu karet po načtení pásu karet do aplikace Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Příklad načte data z ukázkové databáze Northwind a naplní pole se seznamem a nabídku v aplikaci systém Microsoft Office Outlook. Položky, které vyberete v těchto ovládacích prvcích, automaticky naplní pole jako **na** a **Předmět** v e-mailové zprávě.

Tento návod znázorňuje následující úlohy:

- Vytvořte nový projekt doplňku VSTO pro Outlook.

- Navrhněte vlastní skupinu pásu karet.

- Přidejte vlastní skupinu na integrovanou kartu.

- Aktualizujte ovládací prvky na pásu karet v době běhu.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook

Nejprve vytvořte projekt doplňku VSTO pro Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvořte projekt doplňku VSTO pro Outlook s názvem **Ribbon_Update_At_Runtime**.

2. V dialogovém okně **Nový projekt** vyberte **vytvořit adresář pro řešení**.

3. Uložte projekt do výchozího adresáře projektu.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Návrh vlastní skupiny pásu karet

Pás karet tohoto příkladu se zobrazí, když uživatel vytvoří novou e-mailovou zprávu. Chcete-li vytvořit vlastní skupinu pro pás karet, nejprve přidejte položku pásu karet do projektu a pak Navrhněte skupinu v Návrháři pásu karet. Tato vlastní skupina vám pomůže vygenerovat následující e-mailové zprávy pro zákazníky tím, že z databáze nainstalují názvy a řadí historie.

### <a name="to-design-a-custom-group"></a>Návrh vlastní skupiny

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)**.

3. Změňte název nového pásu karet na **CustomerRibbon**a pak klikněte na **Přidat**.

     Otevře se soubor *CustomerRibbon.cs* nebo *CustomerRibbon. vb* v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

4. Kliknutím vyberte Návrhář pásu karet.

5. V okně **vlastnosti** klikněte na šipku rozevíracího seznamu vedle vlastnosti **RibbonType** a pak klikněte na **Microsoft. Outlook. mail.** Form.

     To umožňuje, aby se pás karet zobrazil, když uživatel vytvoří novou e-mailovou zprávu v aplikaci Outlook.

6. V Návrháři pásu karet klikněte na **Group1** a vyberte ho.

7. V okně **vlastnosti** nastavte **popisek** na **nákupy zákazníků**.

8. Na kartě **ovládací prvky pásu karet sady Office** přetáhněte pole **se** **seznamem** na skupinu **nákupu zákazníka** .

9. Klikněte na **ComboBox1** a vyberte ji.

10. V okně **vlastnosti** nastavte **popisek** na **zákazníci**.

11. Na kartě **ovládací prvky pásu karet Office** v **panelu nástrojů**přetáhněte **nabídku** na skupinu **nákupů zákazníků** .

12. V okně **vlastnosti** nastavte **popisek** na **koupený produkt**.

13. Nastavte **dynamické** na **true**.

     To umožňuje přidat a odebrat ovládací prvky v nabídce v době běhu po načtení pásu karet do aplikace Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Přidat vlastní skupinu na integrovanou kartu

Integrovaná karta je karta, která je již na pásu karet v aplikaci Outlook Explorer nebo v nástroji Inspector. V tomto postupu přidáte vlastní skupinu na integrovanou kartu a pak na kartě zadáte pozici vlastní skupiny.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Přidání vlastní skupiny na integrovanou kartu

1. Klikněte na kartu **TabAddins (integrovaná)** a vyberte ji.

2. V okně **vlastnosti** rozbalte vlastnost **ControlID** a pak nastavte **OfficeId** na **TabNewMailMessage**.

     Tím se skupina **koupit zákazníky** přidá na kartu **zprávy** na pásu karet, která se zobrazí v nové e-mailové zprávě.

3. Kliknutím vyberte skupinu **koupit zákazníky** .

4. V okně **vlastnosti** rozbalte vlastnost **pozice** , klikněte na šipku rozevíracího seznamu vedle vlastnosti **PositionType** a potom klikněte na možnost **BeforeOfficeId**.

5. Nastavte vlastnost **OfficeId** na **GroupClipboard**.

     Tím se skupina **nákupů zákazníků** před skupinou **schránek** karty **zprávy** umístí.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Pomocí okna **zdroje dat** přidejte do projektu typovou datovou sadu.

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

     Spustí se **Průvodce konfigurací zdroje dat**.

2. Vyberte **databáze**a pak klikněte na **Další**.

3. Vyberte **datová sada**a potom klikněte na **Další**.

4. Vyberte datové připojení k ukázkové databázi Northwind Microsoft SQL Server Compact 4,0 nebo přidejte nové připojení pomocí tlačítka **nové připojení** .

5. Po vybrání nebo vytvoření připojení klikněte na **Další**.

6. Kliknutím na tlačítko **Další** uložte připojovací řetězec.

7. Na stránce **zvolit databázové objekty** rozbalte **tabulky**.

8. Zaškrtněte políčko vedle každé z následujících tabulek:

    1. **Zákazníci**

    2. **Podrobnosti objednávky**

    3. **Orders (Objednávky)**

    4. **Produkty**

9. Klikněte na **Finish** (Dokončit).

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Aktualizovat ovládací prvky ve vlastní skupině v době běhu

Pomocí objektového modelu pásu karet proveďte následující úlohy:

- Přidejte jména zákazníků do pole se seznamem **zákazníci** .

- Přidejte ovládací prvky nabídky a tlačítka do nabídky **zakoupených produktů** , které reprezentují prodejní objednávky a prodávané produkty.

- Vyplňte pole do, předmět a text nových poštovních zpráv pomocí dat z nabídky se seznamem **zákazníků** a **zakoupených produktů** .

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Aktualizace ovládacích prvků ve vlastní skupině pomocí modelu objektů pásu karet

1. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **.NET** , vyberte sestavení **System. data. Linq** a pak klikněte na tlačítko **OK**.

    Toto sestavení obsahuje třídy pro použití Language-Integratedch dotazů (LINQ). Pomocí LINQ budete naplnit ovládací prvky ve vlastní skupině daty z databáze Northwind.

3. V **Průzkumník řešení**pro výběr klikněte na **CustomerRibbon.cs** nebo **CustomerRibbon. vb** .

4. V nabídce **zobrazení** klikněte na příkaz **Code (kód**).

    V editoru kódu se otevře soubor kódu pásu karet.

5. Přidejte následující příkazy do horní části souboru kódu pásu karet. Tyto příkazy poskytují snadný přístup k oborům názvů LINQ a k oboru názvů primárního definičního sestavení (PIA) aplikace Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Do třídy přidejte následující kód `CustomerRibbon` . Tento kód deklaruje adaptéry tabulky dat a tabulky, které použijete k uložení informací z tabulek, objednávek, podrobností objednávky a produktů z databáze Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Do třídy přidejte následující blok kódu `CustomerRibbon` . Tento kód přidá tři pomocné metody, které vytvoří ovládací prvky pro pás karet v době běhu.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. `CustomerRibbon_Load`Metodu obslužné rutiny události nahraďte následujícím kódem. Tento kód používá dotaz LINQ k provádění následujících úloh:

   - Naplňte pole se seznamem **Customers** pomocí ID a názvu 20 zákazníků v databázi Northwind.

   - Volá `PopulateSalesOrderInfo` pomocnou metodu. Tato metoda aktualizuje nabídku **ProductsPurchased** o čísla prodejních objednávek, která se vztahují k aktuálně vybranému zákazníkovi.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Do třídy `CustomerRibbon` přidejte následující kód. Tento kód používá dotazy LINQ k provádění následujících úloh:

   - Přidá podnabídku do nabídky **ProductsPurchased** pro každé prodejní objednávky související s vybraným zákazníkem.

   - Přidá tlačítka do každé podnabídky pro produkty, které se vztahují k prodejní objednávce.

   - Přidá obslužné rutiny události pro každé tlačítko.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. V **Průzkumník řešení**dvakrát klikněte na soubor kódu pásu karet.

     Otevře se Návrhář pásu karet.

11. V Návrháři pásu karet poklikejte na pole se seznamem **zákazníci** .

     V editoru kódu se otevře soubor kódu pásu karet a `ComboBox1_TextChanged` zobrazí se obslužná rutina události.

12. Proměnnou `ComboBox1_TextChanged` obslužné rutiny události nahraďte následujícím kódem. Tento kód provádí následující úlohy:

    - Volá `PopulateSalesOrderInfo` pomocnou metodu. Tato metoda aktualizuje nabídku **koupené produkty** prodejními objednávkami, které se vztahují k vybranému zákazníkovi.

    - Zavolá `PopulateMailItem` pomocnou metodu a předá do aktuálního textu, který je vybraný název zákazníka. Tato metoda naplní pole pro, předmět a text nových e-mailových zpráv.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Přidejte `Click` do třídy následující obslužnou rutinu události `CustomerRibbon` . Tento kód přidá názvy vybraných produktů do pole text v nových poštovních zprávách.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Do třídy `CustomerRibbon` přidejte následující kód. Tento kód provádí následující úlohy:

    - Naplní do řádku nové e-mailové zprávy pomocí e-mailové adresy aktuálně vybraného zákazníka.

    - Přidá text do polí předmět a text nové e-mailové zprávy.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testování ovládacích prvků ve vlastní skupině

Když v aplikaci Outlook otevřete nový formulář pošty, na kartě **zprávy** na pásu karet se zobrazí vlastní skupina s názvem **nákupy zákazníků** .

Pokud chcete vytvořit informovou e-mailovou zprávu zákazníka, vyberte zákazníka a pak vyberte produkty zakoupené zákazníkem. Ovládací prvky ve skupině **nákupů zákazníků** se aktualizují za běhu s daty z databáze Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Testování ovládacích prvků ve vlastní skupině

1. Stisknutím klávesy **F5** spusťte projekt.

     Spustí se aplikace Outlook.

2. V aplikaci Outlook v nabídce **soubor** přejděte na příkaz **Nový**a poté klikněte na položku **poštovní zpráva**.

     Provedou se následující akce:

    - Zobrazí se okno pro zobrazení nového e-mailové zprávy.

    - Na kartě **zpráva** na pásu karet se skupina **Nákup zákazníka** zobrazí před skupinou **schránky** .

    - Pole se seznamem **zákazníci** ve skupině se aktualizuje o jména zákazníků v databázi Northwind.

3. Na kartě **zpráva** na pásu karet ve skupině **Nákup zákazníka** vyberte zákazníka v poli se seznamem **Customers (zákazníci** ).

     Provedou se následující akce:

    - Nabídka **zakoupených produktů** se aktualizuje a zobrazí se všechny prodejní objednávky vybraného zákazníka.

    - V podnabídce každá prodejní objednávka se aktualizuje, aby se zobrazily produkty zakoupené v tomto pořadí.

    - E-mailová adresa vybraného zákazníka se přidá na řádek **do** řádku e-mailové zprávy a předmět a text e-mailové zprávy se naplní textem.

4. Klikněte na nabídku **Nákup produktů** , přejděte na položku jakákoli prodejní objednávka a pak klikněte na produkt z prodejní objednávky.

     Název produktu se přidá do textu e-mailové zprávy.

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak přizpůsobit uživatelské rozhraní Office, najdete v těchto tématech:

- Přidejte kontextové uživatelské rozhraní do libovolného přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

- Rozšíříte standardní nebo vlastní systém Microsoft Office formulář aplikace Outlook. Další informace najdete v tématu [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Přidejte vlastní podokno úloh do Outlooku. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Viz také

- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)
- [Přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Postupy: zobrazení chyb uživatelského rozhraní doplňku](../vsto/how-to-show-add-in-user-interface-errors.md)