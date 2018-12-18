---
title: 'Návod: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18848f0ebd6ffa289ea09553de82f5b9eb893181
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295836"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Návod: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat

Služba obchodní Data připojení (BDC) umožňuje SharePoint k zobrazení obchodní data z back endové serverové aplikace, webové služby a databáze.

Tento návod ukazuje, jak vytvořit model služby BDC, který vrací informace o kontaktech ve vzorové databázi. Pak vytvoříte externí seznam na Sharepointu pomocí tohoto modelu.

Tento návod znázorňuje následující úlohy:

- Vytvoření projektu.
- Přidání entity do modelu.
- Přidání vyhledávací metody.
- Přidání konkrétní vyhledávací metody.
- Testování projektu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice systému Windows a SharePoint.

- Přístup k ukázkové databázi AdventureWorks. Další informace o tom, jak nainstalovat databázi AdventureWorks, naleznete v tématu [ukázkové databáze systému SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="create-a-project-that-contains-a-bdc-model"></a>Vytvořit projekt, který obsahuje model služby BDC

1. V panelu nabídek v sadě Visual Studio zvolte **souboru** > **nový** > **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

2. V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** položky.

3. V **šablony** podokně zvolte **projektu služby SharePoint 2010**, pojmenujte projekt **AdventureWorksTest**a klikněte na tlačítko **OK** tlačítko .

     **Průvodce přizpůsobením SharePoint** se zobrazí. V tomto průvodci můžete zadat web, který budete používat k ladění projektu a nastavte úroveň důvěryhodnosti řešení.

4. Zvolte **nasadit jako řešení farmy** přepínač nastavit úroveň důvěryhodnosti.

5. Zvolte **Dokončit** tlačítko k přijetí výchozího místního webu služby SharePoint.

6. V **Průzkumníka řešení**, zvolte uzel projektu služby SharePoint.

7. V panelu nabídky zvolte **projektu** > **přidat novou položku**.

     **Přidat novou položku** zobrazí se dialogové okno.

8. V **šablony** podokně zvolte **Model Připojení obchodních dat (pouze řešení farmy)**, pojmenujte projekt **AdventureWorksContacts**a klikněte na tlačítko **Přidat** tlačítko.

## <a name="add-data-access-classes-to-the-project"></a>Přidání tříd pro přístup k data do projektu

1. V panelu nabídky zvolte **nástroje** > **připojit k databázi**.

     **Přidat připojení** zobrazí se dialogové okno.

2. Přidání připojení k ukázkové databázi AdventureWorks SQL serveru.

     Další informace najdete v tématu [přidat/změnit připojení (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. V **Průzkumníka řešení**, zvolte uzel projektu.

4. V panelu nabídky zvolte **projektu** > **přidat novou položku**.

5. V **nainstalované šablony** podokně, vyberte **Data** uzlu.

6. V **šablony** podokně zvolte **třídy LINQ to SQL**.

7. V **název** zadejte **AdventureWorks**a klikněte na tlačítko **přidat** tlačítko.

     Souboru .dbml je přidán do projektu a otevře se Návrhář relací objektů (O/R Designer).

8. V panelu nabídky zvolte **zobrazení** > **Průzkumníka serveru**.

9. V **Průzkumníka serveru**, rozbalte uzel, který představuje ukázkovou databází AdventureWorks a potom rozbalte **tabulky** uzlu.

10. Přidat **kontakt (osoba)** tabulky do Návrháře relací objektů.

     Třídu entity se vytvoří a zobrazí na návrhové ploše. Třída entity má vlastnosti, které se mapují na sloupce v tabulce Kontakt (osoba).

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Odebrání výchozí entity z modelu služby BDC

**Model Připojení obchodních dat** projektu přidá výchozí entity do modelu s názvem Entity1. Odeberte tuto entitu. Později přidejte novou entitu. Počínaje prázdný model snižuje počet kroků potřebných k dokončení návodu.

1. V **Průzkumníka řešení**, rozbalte **BdcModel1** uzlu a pak otevřete *BdcModel1.bdcm* souboru.

2. Soubor modelu připojení obchodních dat se otevře v Návrháři služby BDC.

3. V Návrháři otevřete místní nabídku pro **Entity1**a klikněte na tlačítko **odstranit**.

4. V **Průzkumníka řešení**, otevřete místní nabídku pro *Entity1.vb* (v jazyce Visual Basic) nebo *Entity1.cs* (v jazyce C#) a klikněte na tlačítko **odstranit** .

5. Otevřete místní nabídku pro *Entity1Service.vb* (v jazyce Visual Basic) nebo *Entity1Service.cs* (v jazyce C#) a klikněte na tlačítko **odstranit**.

## <a name="add-an-entity-to-the-model"></a>Přidání entity do modelu

Přidání entity do modelu. Můžete přidat entit ze sady Visual Studio **nástrojů** na návrháři služby BDC.

1. V panelu nabídky zvolte **zobrazení** > **nástrojů**.

2. Na **služby Připojení obchodních dat** karty **nástrojů**, přidejte **Entity** na návrháři služby BDC.

     Nová entita se zobrazí v návrháři. Visual Studio přidá soubor s názvem *EntityService.vb* (v jazyce Visual Basic) nebo *EntityService.cs* (v jazyce C#) do projektu.

3. V panelu nabídky zvolte **zobrazení** > **vlastnosti** > **okno**.

4. V **vlastnosti** okno, nastaveno **název** hodnoty vlastnosti **kontakt**.

5. V Návrháři otevřete místní nabídku pro entitu, zvolte **přidat**a klikněte na tlačítko **identifikátor**.

     Nový identifikátor se zobrazí v entitě.

6. V **vlastnosti** okna, změňte název identifikátor, který **KódKontaktu**.

7. V **název typu** klikněte na položku **System.Int32**.

## <a name="add-a-specific-finder-method"></a>Přidání konkrétní vyhledávací metody

Chcete-li služba BDC pro zobrazení konkrétního kontaktu, je nutné přidat metody Specific Finder. Služba BDC volá metody Specific Finder, když uživatel vybere položku v seznamu a následně klikne **položka zobrazení** tlačítko na pásu karet.

Přidání konkrétní vyhledávací metody k entitě kontakt s použitím **podrobnosti metody služby BDC** okna. Pokud chcete vrátit na konkrétní entitu, přidejte kód do metody.

1. V Návrháři služby BDC, zvolte **kontakt** entity.

2. V panelu nabídky zvolte **zobrazení** > **ostatní Windows** > **podrobnosti metody služby BDC**.

     Otevře se okno Podrobnosti metody služby BDC.

3. V **přidejte metodu** klikněte na položku **vytvořit konkrétní metodu Finder**.

     Visual Studio přidá následující prvky modelu. Tyto prvky se zobrazí v **podrobnosti metody služby BDC** okna.

    - Metodu s názvem ReadItem.

    - Vstupní parametr metody.

    - Návratový parametr metody.

    - Popisovač typu pro každý parametr.

    - Instance metody k metodě.

4. V **podrobnosti metody služby BDC** okno, otevřete seznam, který se zobrazí pro **kontakt** popisovač typu a klikněte na tlačítko **upravit**.

     **Služby BDC Explorer** otevře a obsahuje hierarchické zobrazení modelu.

5. V **vlastnosti** okno, otevřete seznam vedle položky **TypeName** vlastnost, zvolte **aktuální projekt** kartu a klikněte na tlačítko **kontakt**vlastnost.

6. V **služby BDC Explorer**, otevřete místní nabídku **kontakt**a klikněte na tlačítko **přidat popisovač typu**.

     Nový typ popisovače, který je pojmenován **TypeDescriptor1** se zobrazí v **služby BDC Explorer**.

7. V **vlastnosti** okno, nastaveno **název** hodnoty vlastnosti **KódKontaktu**.

8. Otevřete seznam vedle položky **TypeName** vlastnost a klikněte na tlačítko **Int32**.

9. Otevřete seznam vedle položky **identifikátor** vlastnost a klikněte na tlačítko **KódKontaktu**.

10. Zopakujte krok 6 k vytvoření popisovače typu pro každý z těchto polí.

    |Název|Název typu|
    |----------|---------------|
    |Jméno|System.String|
    |Příjmení|System.String|
    |Telefon|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. V Návrháři služby BDC na **kontakt** entity, otevřete **ReadItem** metody.

     Soubor kódu služby kontakt se otevře v editoru kódu.

12. V `ContactService` třídy, nahraďte `ReadItem` metodu s následujícím kódem. Tento kód provede následující:

    - Načte záznam z tabulky. Obraťte se databáze AdventureWorks.

    - Vrátí entitu kontakt služby BDC.

    > [!NOTE]
    > Nahraďte hodnotu `ServerName` pole s názvem vašeho serveru.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Přidání vyhledávací metody

Chcete-li služba BDC v seznamu zobrazíte kontakty, je nutné přidat vyhledávací metody. Přidání vyhledávací metody k entitě kontakt s použitím **podrobnosti metody služby BDC** okna. Vrátit kolekci entit do služby BDC, přidejte kód do metody.

1. V Návrháři služby BDC **kontakt** entity.

2. V **podrobnosti metody služby BDC** okně sbalit **ReadItem** uzlu.

3. V **přidejte metodu** seznamu v části **ReadList** metody, zvolte **vytvořit metodu Finder**.

     Visual Studio přidá metodu, návratový parametr a typ popisovače.

4. V Návrháři služby BDC na **kontakt** entity, otevřete **ReadList** metody.

     Soubor kódu služby kontaktů se otevře v editoru kódu.

5. V `ContactService` třídy, nahraďte `ReadList` metodu s následujícím kódem. Tento kód provede následující:

   - Načte data z tabulky kontaktů databáze AdventureWorks.

   - Vrátí seznam entit, kontaktujte služby BDC.

     > [!NOTE]
     > Nahraďte hodnotu `ServerName` pole s názvem vašeho serveru.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Testování projektu

Při spuštění projektu se otevře web služby SharePoint a Visual Studio přidá do služby Připojení obchodních dat modelu. Vytvořte externí seznam na Sharepointu, který odkazuje na entitu kontakt. V seznamu se zobrazí data pro kontakty v databázi AdventureWorks.

> [!NOTE]
> Budete muset změnit nastavení zabezpečení ve službě SharePoint než můžete ladit vaše řešení. Další informace najdete v tématu [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Zvolte **F5** klíč.

     Otevře se web služby SharePoint.

2. Na **Akce webu** nabídek, zvolte **další možnosti** příkazu.

3. Na **vytvořit** zvolte **externí seznam** šablony a klikněte na tlačítko **vytvořit** tlačítko.

4. Název vlastního seznamu **kontakty**.

5. Klikněte na tlačítko Procházet vedle **externího typu obsahu** pole.

6. V **výběr externích typů obsahu** dialogového okna zvolte **AdventureWorksContacts.BdcModel1.Contact** položku a klikněte na tlačítko **vytvořit** tlačítko.

     SharePoint vytvoří externí seznam, který obsahuje kontakty z ukázkové databáze AdventureWorks.

7. Do metody Specific Finder, zvolte v seznamu kontakt.

8. Na pásu karet, zvolte **položky** kartu a klikněte na tlačítko **položka zobrazení** příkazu.

     Podrobnosti kontaktu, který jste zvolili, který se zobrazí ve formuláři.

## <a name="next-steps"></a>Další kroky

Další informace o navrhování modelů služby BDC v Sharepointu v těchto tématech:

- [Postupy: přidání metody vytvoření](../sharepoint/how-to-add-a-creator-method.md).
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md).
- [Postupy: přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Viz také:

[Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)  
[Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)  
[Přehled nástroje pro navrhování modelů služby BDC](../sharepoint/bdc-model-design-tools-overview.md)  
[Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
