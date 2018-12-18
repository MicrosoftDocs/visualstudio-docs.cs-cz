---
title: 'Návod: Aktualizace ovládacích prvků na pásu karet za běhu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 40072b1dcd6b24f552a3c87c8241ea4498229053
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389147"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Návod: Aktualizace ovládacích prvků na pásu karet za běhu

Tento návod ukazuje, jak použít model objektu pásu karet po načtení pásu do aplikace sady Office aktualizace ovládacích prvků na pásu karet.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

V příkladu si vyžádá data z ukázkové databáze Northwind k naplnění pole se seznamem a nabídky v aplikaci Microsoft Office Outlook. Položky, které vyberete v těchto ovládacích prvků, automaticky vyplnit pole, jako **k** a **subjektu** v e-mailovou zprávu.

Tento návod znázorňuje následující úlohy:

-   Vytvoření nového projektu doplňku VSTO v Outlooku.

-   Navrhněte vlastní skupiny pásu karet.

-   Přidáte vlastní skupinu k předdefinované kartě.

-   Aktualizujte ovládací prvky na pásu karet za běhu.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Outlook

Nejprve vytvořte projekt doplňku VSTO v Outlooku.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Outlook

1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvoření projektu doplňku VSTO pro Outlook s názvem **Ribbon_Update_At_Runtime**.

2.  V **nový projekt** dialogu **vytvořit adresář pro řešení**.

3.  Uložte projekt do výchozí adresář projektu.

     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Navrhněte vlastní skupiny pásu karet

Na pásu karet v tomto příkladu se zobrazí, když uživatel vytvoří novou e-mailovou zprávu. Pokud chcete vytvořit vlastní skupiny pásu karet, nejprve přidat položku pásu karet do projektu a návrh skupiny v Návrháři pásu karet. Tuto vlastní skupinu vám pomůže generovat zpracování e-mailové zprávy pro zákazníky díky přebírání názvy a pořadí historie z databáze.

### <a name="to-design-a-custom-group"></a>Chcete-li navrhnout vlastní skupiny

1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.

2.  V **přidat novou položku** dialogu **pás karet (vizuální návrhář)**.

3.  Změňte název nového pásu karet na **CustomerRibbon**a potom klikněte na tlačítko **přidat**.

     *CustomerRibbon.cs* nebo *CustomerRibbon.vb* soubor se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

4.  Klikněte na Návrhář pásu karet vyberte.

5.  V **vlastnosti** okna, klikněte na šipku rozevíracího seznamu vedle položky **RibbonType** vlastnosti a pak klikněte na tlačítko **Microsoft.Outlook.Mail.Compose**.

     To umožňuje pásu karet a zobrazí, když uživatel vytvoří novou e-mailovou zprávu v Outlooku.

6.  V Návrháři pásu karet klikněte na tlačítko **Group1** ji vyberte.

7.  V **vlastnosti** okno, nastavte **popisek** k **nákupech zákazníků**.

8.  Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte **– pole se seznamem** na **nákupech zákazníků** skupiny.

9. Klikněte na tlačítko **ComboBox1** ji vyberte.

10. V **vlastnosti** okno, nastavte **popisek** k **zákazníkům**.

11. Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte **nabídky** na **nákupech zákazníků** skupiny.

12. V **vlastnosti** okno, nastavte **popisek** k **produkt zakoupen**.

13. Nastavte **dynamické** k **true**.

     To umožňuje přidávat a odebírat ovládacích prvků za běhu v nabídce po načtení pásu do aplikace sady Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Přidat vlastní skupinu k předdefinované kartě

Vestavěná karta je kartu, která je již na pásu karet Outlooku Průzkumníka nebo Inspector. V tomto postupu přidáte vlastní skupiny k předdefinované kartě a pak zadejte umístění vlastní skupinu na kartě.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Chcete-li přidat vlastní skupiny k předdefinované kartě

1.  Klikněte na tlačítko **TabAddins (vestavěné)** kartu a vyberte ji.

2.  V **vlastnosti** okna, rozbalte **ControlId** vlastnost a poté nastavte **OfficeId** k **TabNewMailMessage**.

     Tím se přidá **nákupech zákazníků** do **zprávy** kartu pásu karet, který se zobrazí nové e-mailovou zprávu.

3.  Klikněte na tlačítko **nákupech zákazníků** skupina a vyberte ji.

4.  V **vlastnosti** okna, rozbalte **pozice** vlastnosti, klikněte na šipku rozevíracího seznamu vedle položky **PositionType** vlastnosti a pak klikněte na tlačítko  **BeforeOfficeId**.

5.  Nastavte **OfficeId** vlastnost **GroupClipboard**.

     To umístí **nákupech zákazníků** skupiny před **schránky** skupinu **zprávy** kartu.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat

Použití **zdroje dat** okno pro přidání typové datové sady do projektu.

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1.  Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat**.

     Tím se spustí **Průvodce konfigurací zdroje dat**.

2.  Vyberte **databáze**a potom klikněte na tlačítko **Další**.

3.  Vyberte **datovou sadu**a potom klikněte na tlačítko **Další**.

4.  Vyberte datové připojení k Microsoft SQL Server Compact 4.0 ukázkové databáze Northwind, nebo přidejte nové připojení s použitím **nové připojení** tlačítko.

5.  Po připojení se vyberete nebo vytvoříte, klikněte na tlačítko **Další**.

6.  Klikněte na tlačítko **Další** uložit připojovací řetězec.

7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky**.

8.  Zaškrtněte políčko vedle každého z následujících tabulek:

    1.  **Zákazníci**

    2.  **Podrobnosti objednávky**

    3.  **Objednávky**

    4.  **Produkty**

9. Klikněte na tlačítko **Dokončit**.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Aktualizovat ovládací prvky ve vlastní skupině za běhu

Pomocí modelu objektů pásu karet provádět následující úlohy:

-   Přidání názvů zákazníka k **zákazníkům** – pole se seznamem.

-   Přidání ovládacích prvků do nabídky a tlačítko **zakoupených produktů** nabídky, která představují prodejních objednávek a produkty prodávané.

-   Naplnění Komu, předmět a text pole s použitím dat z nového e-mailové zprávy **zákazníkům** – pole se seznamem a **zakoupených produktů** nabídky.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Aktualizace ovládacích prvků ve vlastní skupině pomocí objektového modelu pásu karet

1. Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.

2. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET** kartu, vyberte možnost **System.Data.Linq** sestavení a pak klikněte na tlačítko **OK**.

    Toto sestavení obsahuje třídy pro používání dotazů LINQ (Language Integrated). LINQ použije k vyplnění ovládacích prvků ve vlastní skupině s daty z databáze Northwind.

3. V **Průzkumníka řešení**, klikněte na tlačítko **CustomerRibbon.cs** nebo **CustomerRibbon.vb** ji vyberte.

4. Na **zobrazení** nabídky, klikněte na tlačítko **kód**.

    Soubor kódu pásu karet se otevře v editoru kódu.

5. Přidejte následující příkazy k hornímu okraji soubor kódu pásu karet. Tyto příkazy poskytování snadného přístupu k LINQ obory názvů a názvů Outlook primární definiční sestavení (PIA).

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Přidejte následující kód `CustomerRibbon` třídy. Tento kód deklaruje tabulka dat a adaptérů tabulek, které budete používat k ukládání informací z zákazníky, objednávky, podrobnosti objednávky a tabulky produktů databáze Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Přidejte následující blok kódu, který `CustomerRibbon` třídy. Tento kód přidá tři metody pomocné rutiny, které vytvářejí ovládacích prvků pásu karet za běhu.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Nahradit `CustomerRibbon_Load` metoda obslužné rutiny události s následujícím kódem. Tento kód používá dotaz LINQ provádět následující úlohy:

   - Naplnění **zákazníkům** – pole se seznamem s použitím ID a název 20 zákazníků v databázi Northwind.

   - Volání `PopulateSalesOrderInfo` Pomocná metoda. Tato metoda aktualizuje **ProductsPurchased** nabídky s prodejní objednávky čísla, která se týkají aktuálně vybraného zákazníka.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Přidejte následující kód, který `CustomerRibbon` třídy. Tento kód používá LINQ dotazy pro provádět následující úlohy:

   - Přidá podnabídku **ProductsPurchased** nabídku pro každou prodejní objednávku týkající se k vybranému zákazníkovi.

   - Přidá tlačítka na každé podnabídky pro produkty související s prodejní objednávku.

   - Přidá obslužných rutin událostí do každé tlačítko.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. V **Průzkumníka řešení**, poklikejte na soubor kódu pásu karet.

     Otevře se Návrhář pásu karet.

11. V Návrháři pásu karet klikněte dvakrát na **zákazníkům** – pole se seznamem.

     Soubor kódu pásu karet se otevře v editoru kódu a `ComboBox1_TextChanged` obslužná rutina události se zobrazí.

12. Nahradit `ComboBox1_TextChanged` obslužné rutiny události s následujícím kódem. Tento kód provede následující:

    - Volání `PopulateSalesOrderInfo` Pomocná metoda. Tato metoda aktualizuje **zakoupených produktů** nabídky s prodejní objednávky, které se vztahují k vybranému zákazníkovi.

    - Volání `PopulateMailItem` pomocnou metodu a předá do aktuální textu, což je název vybraného zákazníka. Tato metoda vyplní Komu, předmět a text pole nové e-mailové zprávy.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Přidejte následující `Click` obslužnou rutinu události `CustomerRibbon` třídy. Tento kód přidá název vybrané produkty do pole text z nového e-mailové zprávy.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Přidejte následující kód, který `CustomerRibbon` třídy. Tento kód provede následující:

    - Naplní na řádku nové e-mailové zprávy pomocí e-mailovou adresu aktuálně vybraného zákazníka.

    - Přidá text do pole Předmět a text z nového e-mailové zprávy.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testování ovládacích prvků do vlastní skupiny

Při otevření nového e-mailu formuláře v Outlooku, vytvoří vlastní skupina s názvem **nákupech zákazníků** se zobrazí na **zprávy** kartu na pásu karet.

K vytvoření zprávy e-maily s reakcí zákazníků, vyberte zákazníka a pak vyberte produkty zakoupené zákazníka. Ovládací prvky **nákupech zákazníků** skupiny se aktualizují za běhu pomocí dat z databáze Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Pro testování ovládacích prvků do vlastní skupiny

1.  Stisknutím klávesy **F5** ke spuštění projektu.

     Spuštění aplikace Outlook.

2.  V aplikaci Outlook na **souboru** nabídky, přejděte na **nový**a potom klikněte na tlačítko **e-mailovou zprávu**.

     Dojde k následujícím akcím:

    -   Zobrazí se nové okno inspektoru zprávy e-mailu.

    -   Na **zpráva** kartu na pásu karet **nákupech zákazníků** skupiny se zobrazí před **schránky** skupiny.

    -   **Zákazníkům** – pole se seznamem ve skupině se aktualizuje s názvy zákazníků v databázi Northwind.

3.  Na **zpráva** kartu na pásu karet v **nákupech zákazníků** skupiny, vyberte zákazníka z **zákazníkům** – pole se seznamem.

     Dojde k následujícím akcím:

    -   **Zakoupených produktů** nabídky se aktualizuje a zobrazí jednotlivé prodejní objednávky pro vybraného zákazníka.

    -   Každé podnabídky prodejní objednávky se aktualizuje a zobrazí produkty zakoupené v tomto pořadí.

    -   Vybraného zákazníka e-mailová adresa se přidá do **k** zaplnění řádek e-mailovou zprávu a předmět a text e-mailovou zprávu s textem.

4.  Klikněte na tlačítko **nákup produktů** nabídky, přejděte na příkaz všechny prodejní objednávky a klikněte na produkt z prodejní objednávku.

     Název produktu je přidat k tělu e-mailové zprávě.

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak přizpůsobit uživatelské rozhraní sady Office naleznete v těchto tématech:

-   Přidejte uživatelské rozhraní založené na kontextu do jakéhokoli přizpůsobení úrovni dokumentu. Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).

-   Rozšiřte standardní nebo vlastní formulář aplikace Microsoft Office Outlook. Další informace najdete v tématu [návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md).

-   Přidání vlastního podokna úloh do aplikace Outlook. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Viz také:

- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)
- [Přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Postupy: Add-in zobrazení chyb uživatelského rozhraní](../vsto/how-to-show-add-in-user-interface-errors.md)