---
title: 'Návod: Vytvoření webové části pro SharePoint | Dokumentace Microsoftu'
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
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09b9299c6428ef63ccf71220fc3cb599e9e3b5a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872405"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Návod: Vytvoření webové části pro SharePoint

Webové části umožní uživatelům přímo upravit obsah, vzhled a chování stránky webu služby SharePoint pomocí prohlížeče. Tento návod ukazuje, jak vytvořit webovou část pomocí **webové části** šablony položky v sadě Visual Studio 2010.

Webová část zobrazuje zaměstnancům v datové mřížce. Uživatel Určuje umístění souboru, který obsahuje data zaměstnanců. Uživatele můžete také filtrovat datovou mřížku tak, aby zaměstnanci, kteří jsou správci se zobrazí v seznamu pouze.

Tento návod znázorňuje následující úlohy:

- Vytvoření webové části pomocí sady Visual Studio **webové části** šablony položky.

- Vytvoření vlastnosti můžete nastavit uživatele webové části. Tato vlastnost určuje umístění souboru dat zaměstnance.

- Určuje kolekci, vykreslování obsahu ve webové části přidáním ovládacích prvků do webové části.

- Vytvoření nové položky nabídky, označuje jako *sloveso,* , který se zobrazí v nabídce příkazů vykreslené webové části. Příkazy Povolit uživateli měnit data, která se zobrazí ve webové části.

- Testování webové části služby SharePoint.

    > [!NOTE]
    > Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky

- Podporované vydání systému Microsoft Windows a SharePoint.

- Visual Studio 2017 nebo služby Azure DevOps.

## <a name="create-an-empty-sharepoint-project"></a>Vytvořit prázdný projekt SharePoint

Nejprve vytvořte prázdný Sharepointového projektu. Později přidáte webovou část do projektu s použitím **webové části** šablony položky.

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocí **spustit jako správce** možnost.

2. Na panelu muže zvolte **souboru** > **nový** > **projektu**.

3. V **nový projekt** dialogového okna rozbalte **SharePoint** uzel v jazyce, který chcete použít a klikněte na tlačítko **2010** uzlu.

4. V **šablony** podokně zvolte **projektu služby SharePoint 2010**a klikněte na tlačítko **OK** tlačítko.

     **Průvodce přizpůsobením SharePoint** se zobrazí. Tento průvodce vám umožní vybrat web, který budete používat k ladění projektu a úroveň důvěryhodnosti řešení.

5. Zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko k přijetí výchozího místního webu služby SharePoint.

## <a name="add-a-web-part-to-the-project"></a>Přidejte do projektu webové části

Přidat **webové části** položky do projektu. **Webové části** přidá soubor kódu webové části. Později přidáte kód do souboru kódu webové části pro vykreslení obsahu webové části.

1. V panelu nabídky zvolte **projektu** > **přidat novou položku**.

2. V **přidat novou položku** v dialogu **nainstalované šablony** podokně rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.

3. V seznamu šablon služby SharePoint, zvolte **webové části** šablony a klikněte na tlačítko **přidat** tlačítko.

     **Webové části** položka je zobrazena v **Průzkumníka řešení**.

## <a name="rendering-content-in-the-web-part"></a>Vykreslování obsahu ve webové části

Můžete určit, jaké ovládací prvky, které se mají zobrazit ve webové části jejich přidáním do kolekce ovládacích prvků webové části třídy.

1. V **Průzkumníka řešení**, otevřete *WebPart1.vb* (v jazyce Visual Basic) nebo *WebPart1.cs* (v jazyce C#).

     Soubor webové části kódu se otevře v editoru kódu.

2. Přidejte následující příkazy do horní části souboru kódu webové části.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Přidejte následující kód, který `WebPart1` třídy. Tento kód deklaruje následující pole:

   - Datová mřížka zobrazíte zaměstnance ve webové části.

   - Text, který se zobrazí v ovládacím prvku, který se používá k filtrování datové mřížce.

   - Popisek, který se zobrazí chyba, pokud je datové mřížce nemůže zobrazit data.

   - Řetězec, který obsahuje cestu k souboru data zaměstnanců.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Přidejte následující kód, který `WebPart1` třídy. Tento kód přidá vlastní vlastnost s názvem `DataFilePath` do webové části. Vlastní vlastnost je vlastnost, která můžete nastavit v Sharepointu uživatelem. Tato vlastnost získá a nastaví umístění datového souboru XML, který se používá k naplnění datové mřížce.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Nahradit `CreateChildControls` metodu s následujícím kódem. Tento kód provede následující:

   - Přidá datovou mřížku a popisek, který je deklarován v předchozím kroku.

   - Vytvoří vazbu mřížky dat do souboru XML, který obsahuje data zaměstnanců.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Přidejte následující metodu do `WebPart1` třídy. Tento kód provede následující:

   - Vytvoří příkaz, který se zobrazí v nabídce příkazů webové části vykresleného webové části.

   - Zpracovává událost, která se vyvolá, když uživatel vybere příkaz v nabídce příkazů. Tento kód filtruje seznam zaměstnanců, která se zobrazí v datové mřížce.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testování webové části

Při spuštění projektu se otevře web služby SharePoint. Webová část je automaticky přidán do Galerie webových částí služby SharePoint. Webové části můžete přidat na libovolnou stránku webové části.

1. Vložte následující kód XML do souboru poznámkového bloku. Tento soubor XML obsahuje ukázková data, která se zobrazí ve webové části.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. V poznámkovém bloku, v řádku nabídek zvolte **souboru** > **uložit jako**.

3. V **uložit jako** v dialogu **uložit jako typ** klikněte na položku **všechny soubory**.

4. V **název_souboru** zadejte **data.xml**.

5. Vyberte libovolnou složku pomocí **procházet složky** tlačítko a klikněte na tlačítko **Uložit** tlačítko.

6. V sadě Visual Studio, zvolte **F5** klíč.

     Otevře se web služby SharePoint.

7. Na **Akce webu** nabídce zvolte **další možnosti**.

8. V **vytvořit** zvolte **stránku webových částí** zadejte a pak zvolte **vytvořit** tlačítko.

9. V **nová stránka webových částí** stránky, zadejte název stránky **SampleWebPartPage.aspx**a klikněte na tlačítko **vytvořit** tlačítko.

     Zobrazí se stránka webové části.

10. Vyberte všechny zóny na stránku webových částí.

11. V horní části stránky zvolte **vložit** kartu a klikněte na tlačítko **webové části** tlačítko.

12. V **kategorie** podokně, vyberte **vlastní** složky, zvolte **WebPart1** webové části a klikněte na tlačítko **přidat** tlačítko.

     Webová část se zobrazí na stránce.

## <a name="test-the-custom-property"></a>Testování vlastní vlastnost

K naplnění mřížky dat, který se zobrazí ve webové části, zadejte cestu k souboru XML, který obsahuje data o jednotliví zaměstnanci.

1. Klikněte na šipku, která se zobrazí na pravé straně webové části a klikněte na tlačítko **upravit webovou část** ze zobrazené nabídky.

     Podokno, které obsahuje vlastnosti pro webovou část se zobrazí na pravé straně stránky.

2. V podokně rozbalte **různé** uzlu, zadejte cestu k souboru XML, který jste vytvořili dříve, zvolte **použít** tlačítko a klikněte na tlačítko **OK** tlačítko.

     Ověřte, že se zobrazí seznam zaměstnanců ve webové části.

## <a name="test-the-web-part-verb"></a>Otestovat operaci webové části

Zobrazení a skrytí zaměstnance, kteří nejsou správci kliknutím na položku, která se zobrazí v nabídce příkazů webových částí.

1. Klikněte na šipku, která se zobrazí na pravé straně webové části a klikněte na tlačítko **zobrazit pouze správci** ze zobrazené nabídky.

     Ve webové části se zobrazí pouze zaměstnanci, kteří jsou správci.

2. Znovu klikněte na šipku a klikněte na tlačítko **zobrazit všichni zaměstnanci** ze zobrazené nabídky.

     Všichni zaměstnanci se zobrazí ve webové části.

## <a name="see-also"></a>Viz také:

[Vytvoření webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Postupy: vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Postupy: vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
