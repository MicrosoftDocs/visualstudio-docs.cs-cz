---
title: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat
description: Vytvořte model služby BDC, který vrací informace o kontaktech v obchodní databázi, a pak vytvořte externí seznam ve službě SharePoint pomocí tohoto modelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0811b029bf7e4705bc0c3689eff73f38280c3b3d
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217681"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Návod: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat

Služba BDC (Business Data Connectivity) umožňuje službě SharePoint zobrazovat obchodní data z back-endové aplikace, webových služeb a databází.

V tomto návodu se dozvíte, jak vytvořit model služby BDC, který vrací informace o kontaktech v ukázkové databázi. Pak vytvoříte externí seznam ve službě SharePoint pomocí tohoto modelu.

Tento návod znázorňuje následující úlohy:

- Vytváření projektu.
- Přidání entity do modelu.
- Přidání vyhledávací metody
- Přidání konkrétní vyhledávací metody
- Testování projektu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Windows a SharePointu.

- Přístup k ukázkové databázi AdventureWorks. Další informace o tom, jak nainstalovat databázi AdventureWorks, najdete v tématu [SQL Server ukázkových databází](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Vytvoření projektu, který obsahuje model služby BDC

1. Na panelu nabídek v aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**.

     Otevře se dialogové okno **Nový projekt** .

2. V části **Visual C#** nebo **Visual Basic** rozbalte uzel **SharePoint** a pak zvolte položku **2010** .

3. V podokně **šablony** zvolte **projekt SharePoint 2010**, pojmenujte projekt **AdventureWorksTest** a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** . V tomto průvodci můžete určit web, který budete používat k ladění projektu a nastavit úroveň důvěryhodnosti řešení.

4. Klikněte na tlačítko možnosti **nasadit jako řešení farmy** a nastavte úroveň důvěryhodnosti.

5. Kliknutím na tlačítko **Dokončit** přijměte výchozí místní web služby SharePoint.

6. V **Průzkumník řešení** vyberte uzel projektu služby SharePoint.

7. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

     Otevře se dialogové okno **Přidat novou položku** .

8. V podokně **šablony** zvolte **Model připojení obchodních dat (pouze řešení farmy)**, pojmenujte projekt **AdventureWorksContacts** a pak klikněte na tlačítko **Přidat** .

## <a name="add-data-access-classes-to-the-project"></a>Přidat třídy přístupu k datům do projektu

1. Na panelu nabídek vyberte **nástroje**  >  **připojit k databázi**.

     Otevře se dialogové okno **Přidat připojení** .

2. Přidejte připojení k ukázkové databázi SQL Server AdventureWorks.

     Další informace najdete v tématu [Přidání nebo úprava připojení (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. V **Průzkumník řešení** vyberte uzel projektu.

4. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

5. V podokně **Nainstalované šablony** vyberte **datový** uzel.

6. V podokně **šablony** vyberte možnost **LINQ to SQL třídy**.

7. V poli **název** zadejte **AdventureWorks** a pak klikněte na tlačítko **Přidat** .

     Do projektu se přidá soubor. dbml a otevře se Návrhář relací objektů (Návrhář O/R).

8. Na panelu nabídek vyberte možnost **Zobrazit**  >  **Průzkumník serveru**.

9. V **Průzkumník serveru** rozbalte uzel reprezentující ukázkovou databázi AdventureWorks a potom rozbalte uzel **tabulky** .

10. Přidejte tabulku **kontaktů (Person)** do návrháře relací výstupů.

     Vytvoří se Třída entity, která se zobrazí na návrhové ploše. Třída entity obsahuje vlastnosti, které jsou mapovány na sloupce v tabulce Contact (osoba).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Odebrání výchozí entity z modelu služby BDC

Projekt **modelu připojení obchodních dat** přidá do modelu výchozí entitu s názvem Entity1. Odeberte tuto entitu. Později budete přidávat novou entitu. Počínaje prázdným modelem se zmenší počet kroků potřebných k dokončení tohoto postupu.

1. V **Průzkumník řešení** rozbalte uzel **BdcModel1** a pak otevřete soubor *BdcModel1. bdcm* .

2. Soubor modelu připojení obchodních dat se otevře v Návrháři služby BDC.

3. V Návrháři otevřete místní nabídku pro **Entity1** a pak zvolte **Odstranit**.

4. V **Průzkumník řešení** otevřete místní nabídku pro *Entity1. vb* (v Visual Basic) nebo *Entity1. cs* (v jazyce C#) a pak zvolte **Odstranit**.

5. Otevřete místní nabídku pro *Entity1Service. vb* (v Visual Basic) nebo *Entity1Service. cs* (v jazyce C#) a pak zvolte **Odstranit**.

## <a name="add-an-entity-to-the-model"></a>Přidání entity do modelu

Přidejte do modelu entitu. Do návrháře služby BDC můžete přidat entity z **panelu nástrojů sady** Visual Studio.

1. Na panelu nabídek vyberte možnost **Zobrazit**  >  **sadu nástrojů**.

2. Na kartě **BusinessDataConnectivity** sady **nástrojů** přidejte **entitu** do návrháře služby BDC.

     Nová entita se zobrazí v návrháři. Visual Studio přidá soubor s názvem *EntityService. vb* (v Visual Basic) nebo *EntityService. cs* (v jazyce C#) do projektu.

3. Na panelu nabídek vyberte možnost **Zobrazit**  >    >  **okno** vlastností.

4. V okně **vlastnosti** nastavte vlastnost **název** na hodnotu **kontakt**.

5. V Návrháři otevřete místní nabídku pro entitu, zvolte možnost **Přidat** a pak zvolte možnost **identifikátor**.

     V entitě se zobrazí nový identifikátor.

6. V okně **vlastnosti** změňte název identifikátoru na **ContactID**.

7. V seznamu **název typu** vyberte **System. Int32**.

## <a name="add-a-specific-finder-method"></a>Přidat konkrétní vyhledávací metodu

Pokud chcete službě BDC povolit zobrazení určitého kontaktu, musíte přidat konkrétní vyhledávací metodu. Služba BDC volá konkrétní vyhledávací metodu, když uživatel zvolí položku v seznamu a pak na pásu karet klikne na tlačítko **Zobrazit položku** .

Přidejte konkrétní vyhledávací metodu k entitě kontakt pomocí okna **Podrobnosti metody služby BDC** . Chcete-li vrátit konkrétní entitu, přidejte kód do metody.

1. V Návrháři BDC vyberte entitu **kontakt** .

2. Na panelu nabídek vyberte **Zobrazit**  >  **Další**  >  **Podrobnosti o metodě služby Windows BDC**.

     Otevře se okno Podrobnosti metody služby BDC.

3. V seznamu **Přidat metodu** vyberte možnost **vytvořit konkrétní vyhledávací metodu**.

     Visual Studio přidá do modelu následující prvky. Tyto prvky se zobrazí v okně **Podrobnosti metody služby BDC** .

    - Metoda s názvem ReadItem.

    - Vstupní parametr pro metodu.

    - Návratový parametr pro metodu.

    - Popisovač typu pro každý parametr.

    - Instance metody pro metodu.

4. V okně **Podrobnosti metody služby BDC** otevřete seznam, který se zobrazí u možnosti popisovač typu **kontaktu** , a pak zvolte **Upravit**.

     Otevře se **Průzkumník služby BDC** , který poskytuje hierarchické zobrazení modelu.

5. V okně **vlastnosti** otevřete seznam vedle vlastnosti **TypeName** , zvolte kartu **aktuální projekt** a pak zvolte vlastnost **kontakt** .

6. V **Průzkumníku služby BDC** otevřete místní nabídku **kontaktu** a zvolte možnost **Přidat popisovač typu**.

     V **Průzkumníkovi služby BDC** se zobrazí nový popisovač typu s názvem **TypeDescriptor1** .

7. V okně **vlastnosti** nastavte vlastnost **název** na hodnotu **ContactID**.

8. Otevřete seznam vedle vlastnosti **TypeName** a pak zvolte **Int32**.

9. Otevřete seznam vedle vlastnosti **identifikátor** a zvolte možnost **ContactID**.

10. Opakujte krok 6 a vytvořte popisovač typu pro každé z následujících polí.

    |Name|Název typu|
    |----------|---------------|
    |FirstName|System. String|
    |LastName|System. String|
    |Rozložení|System. String|
    |EmailAddress|System. String|
    |EmailPromotion|System. Int32|
    |NameStyle|System. Boolean|
    |PasswordHash (Hodnota hash hesla)|System. String|
    |PasswordSalt|System. String|

11. V Návrháři služby BDC v entitě **kontakt** otevřete metodu **ReadItem** .

     Soubor kódu kontaktní služby se otevře v editoru kódu.

12. Ve `ContactService` třídě nahraďte `ReadItem` metodu následujícím kódem. Tento kód provádí následující úlohy:

    - Načte záznam z tabulky kontaktů databáze AdventureWorks.

    - Vrátí entitu kontakt na službu BDC.

    > [!NOTE]
    > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="add-a-finder-method"></a>Přidání vyhledávací metody

Chcete-li povolit službě BDC zobrazení kontaktů v seznamu, je nutné přidat vyhledávací metodu. Přidejte do entity Contact metodu Finder pomocí okna **Podrobnosti metody služby BDC** . Pokud chcete vrátit kolekci entit ke službě BDC, přidejte do metody kód.

1. V Návrháři služby BDC vyberte entitu **kontakt** .

2. V okně **Podrobnosti metody služby BDC** sbalte uzel **ReadItem** .

3. V seznamu **Přidat metodu** v rámci metody **ReadList** vyberte možnost **vytvořit vyhledávací metodu**.

     Visual Studio přidá metodu, návratový parametr a popisovač typu.

4. V Návrháři služby BDC v entitě **kontakt** otevřete metodu **ReadList** .

     Soubor kódu kontaktní služby se otevře v editoru kódu.

5. Ve `ContactService` třídě nahraďte `ReadList` metodu následujícím kódem. Tento kód provádí následující úlohy:

   - Načte data z tabulky kontaktů databáze AdventureWorks.

   - Vrátí seznam entit kontaktů služby BDC.

     > [!NOTE]
     > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="test-the-project"></a>Testování projektu

Při spuštění projektu se otevře web služby SharePoint a Visual Studio přidá váš model do služby připojení obchodních dat. Vytvořte externí seznam na SharePointu, který odkazuje na entitu kontakt. V seznamu se zobrazí data pro kontakty v databázi AdventureWorks.

> [!NOTE]
> Než budete moct řešení ladit, možná budete muset změnit nastavení zabezpečení na SharePointu. Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Klikněte na klávesu **F5** .

     Otevře se web služby SharePoint.

2. V nabídce **Akce webu** klikněte na příkaz **Další možnosti** .

3. Na stránce **vytvořit** vyberte šablonu **externí seznam** a pak klikněte na tlačítko **vytvořit** .

4. Pojmenujte **Kontakty** vlastního seznamu.

5. Klikněte na tlačítko Procházet vedle pole **typ externího obsahu** .

6. V dialogovém okně **Výběr typu externího obsahu** zvolte položku **AdventureWorksContacts. BdcModel1. Contact** a pak klikněte na tlačítko **vytvořit** .

     SharePoint vytvoří externí seznam, který obsahuje kontakty z ukázkové databáze AdventureWorks.

7. Chcete-li otestovat konkrétní vyhledávací metodu, vyberte v seznamu kontakt.

8. Na pásu karet klikněte na kartu **položky** a pak zvolte příkaz **Zobrazit položku** .

     Podrobnosti kontaktu, který jste zvolili, se zobrazí ve formuláři.

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak navrhovat modely pro službu BDC v SharePointu, najdete v těchto tématech:

- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)

## <a name="see-also"></a>Viz také

[Návrh modelu](../sharepoint/designing-a-business-data-connectivity-model.md) 
 Připojení obchodních dat [Vytvoření modelu](../sharepoint/creating-a-business-data-connectivity-model.md) 
 Připojení obchodních dat Přehled nástrojů pro [Návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md) 
 [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)