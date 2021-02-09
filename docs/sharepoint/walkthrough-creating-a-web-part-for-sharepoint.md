---
title: 'Návod: Vytvoření webové části pro SharePoint | Microsoft Docs'
description: Vytvoření webové části pro službu SharePoint. Webové části umožňují uživatelům přímo měnit obsah, vzhled a chování stránek webu služby SharePoint pomocí prohlížeče.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f2d14bfd069fcf5064c9d8643393e28e52570be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918631"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Návod: Vytvoření webové části pro službu SharePoint

Webové části umožnit uživatelům přímo upravovat obsah, vzhled a chování stránek webu SharePoint pomocí prohlížeče. V tomto návodu se dozvíte, jak vytvořit webovou část pomocí šablony položky **webové části** v aplikaci Visual Studio 2010.

Webová část zobrazuje zaměstnance v datové mřížce. Uživatel Určuje umístění souboru, který obsahuje data o zaměstnancích. Uživatel může také filtrovat datovou mřížku tak, aby se zaměstnanci, kteří jsou manažeři, zobrazovali pouze v seznamu.

Tento návod znázorňuje následující úlohy:

- Vytvoření webové části pomocí šablony položky **webové části** sady Visual Studio.

- Vytvoření vlastnosti, kterou může nastavit uživatel webové části. Tato vlastnost určuje umístění datového souboru zaměstnanců.

- Vykreslení obsahu ve webové části přidáním ovládacích prvků do kolekce ovládacích prvků webové části.

- Vytvoření nové položky nabídky označované jako *sloveso* , které se zobrazí v nabídce příkazů vyvykreslované webové části. Příkazy umožňují uživateli upravovat data, která se zobrazí ve webové části.

- Testování webové části ve službě SharePoint.

    > [!NOTE]
    > Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky

- Podporované edice Microsoft Windows a SharePointu.

- Visual Studio 2017 nebo Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Vytvoření prázdného projektu služby SharePoint

Nejprve vytvořte prázdný projekt služby SharePoint. Později přidáte do projektu webovou část pomocí šablony položky **Webová část** .

1. Spusťte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocí možnosti **Spustit jako správce** .

2. Na panelu muži vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzel **služby SharePoint** v jazyce, který chcete použít, a pak vyberte uzel **2010** .

4. V podokně **šablony** zvolte **projekt SharePoint 2010** a pak klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** . Tento průvodce umožňuje vybrat lokalitu, kterou budete používat k ladění projektu a úroveň důvěryhodnosti řešení.

5. Zvolte možnost **nasadit jako řešení farmy** a potom kliknutím na tlačítko **Dokončit** přijměte výchozí místní web služby SharePoint.

## <a name="add-a-web-part-to-the-project"></a>Přidat webovou část do projektu

Přidejte do projektu položku **webové části** . Položka **webové části** přidá soubor kódu webové části. Později přidáte kód do souboru kódu webové části, který vykreslí obsah webové části.

1. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** v podokně **Nainstalované šablony** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

3. V seznamu šablon služby SharePoint vyberte šablonu **webové části** a pak klikněte na tlačítko **Přidat** .

     Položka **webové části** se zobrazí v **Průzkumník řešení**.

## <a name="rendering-content-in-the-web-part"></a>Vykreslování obsahu ve webové části

Můžete určit ovládací prvky, které se mají zobrazit ve webové části, jejich přidáním do kolekce Controls třídy webové části.

1. V **Průzkumník řešení** otevřete *WebPart1. vb* (v Visual Basic) nebo *WebPart1.cs* (v jazyce C#).

     V editoru kódu se otevře soubor kódu webové části.

2. Přidejte následující direktivy do horní části souboru kódu webové části.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Do třídy `WebPart1` přidejte následující kód. Tento kód deklaruje následující pole:

   - Datová mřížka pro zobrazení zaměstnanců ve webové části

   - Text, který se zobrazí na ovládacím prvku, který se používá k filtrování datové mřížky.

   - Popisek, který zobrazí chybu, pokud datová mřížka nemůže zobrazit data.

   - Řetězec, který obsahuje cestu k datovému souboru zaměstnanců.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Do třídy `WebPart1` přidejte následující kód. Tento kód přidá vlastní vlastnost s názvem `DataFilePath` do webové části. Vlastní vlastnost je vlastnost, kterou uživatel může nastavit v SharePointu. Tato vlastnost načte a nastaví umístění datového souboru XML, který se používá k naplnění datové mřížky.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Nahraďte metodu `CreateChildControls` následujícím kódem. Tento kód provádí následující úlohy:

   - Přidá datovou mřížku a popisek, který jste deklarovali v předchozím kroku.

   - Váže datovou mřížku k souboru XML, který obsahuje data o zaměstnancích.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Do třídy přidejte následující metodu `WebPart1` . Tento kód provádí následující úlohy:

   - Vytvoří příkaz, který se zobrazí v nabídce příkazy webové části vykreslené webové části.

   - Zpracovává událost, která je vyvolána, když uživatel zvolí příkaz v nabídce příkazů. Tento kód filtruje seznam zaměstnanců, které se zobrazí v datové mřížce.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testování webové části

Při spuštění projektu se otevře web služby SharePoint. Webová část je automaticky přidána do galerie webových částí v SharePointu. Webovou část můžete přidat na jakoukoli stránku webové části.

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

2. V programu Poznámkový blok v panelu nabídek vyberte **soubor**  >  **Uložit jako**.

3. V dialogovém okně **Uložit jako** v seznamu **Uložit jako typ** vyberte možnost **všechny soubory**.

4. Do pole **název souboru** zadejte **data.xml**.

5. Zvolte libovolnou složku pomocí tlačítka **Procházet složky** a pak klikněte na tlačítko **Uložit** .

6. V aplikaci Visual Studio klikněte na klávesu **F5** .

     Otevře se web služby SharePoint.

7. V nabídce **Akce webu** klikněte na **Další možnosti**.

8. Na stránce **vytvořit** vyberte typ **stránky Webová část** a pak klikněte na tlačítko **vytvořit** .

9. Na stránce **Nová webová část** pojmenujte stránku **SampleWebPartPage. aspx** a pak klikněte na tlačítko **vytvořit** .

     Zobrazí se stránka webová část.

10. Na stránce webové části vyberte libovolnou zónu.

11. V horní části stránky klikněte na kartu **Vložit** a potom klikněte na tlačítko **Webová část** .

12. V podokně **kategorie** zvolte **vlastní** složku, zvolte webovou část **WebPart1** a pak klikněte na tlačítko **Přidat** .

     Webová část se zobrazí na stránce.

## <a name="test-the-custom-property"></a>Test vlastní vlastnosti

Chcete-li naplnit datovou mřížku, která se zobrazí ve webové části, zadejte cestu k souboru XML, který obsahuje data o jednotlivých zaměstnancích.

1. Zvolte šipku, která se zobrazí na pravé straně webové části, a v zobrazené nabídce zvolte **Upravit webovou část** .

     Podokno, které obsahuje vlastnosti webové části, se zobrazí na pravé straně stránky.

2. V podokně rozbalte uzel **různé** , zadejte cestu k souboru XML, který jste vytvořili dříve, klikněte na tlačítko **použít** a pak klikněte na tlačítko **OK** .

     Ověřte, že se ve webové části zobrazuje seznam zaměstnanců.

## <a name="test-the-web-part-verb"></a>Testování příkazu webové části

Umožňuje zobrazit a skrýt zaměstnance, kteří nejsou manažeři, a to tak, že vyberete položku, která se zobrazí v nabídce příkazy webové části.

1. Zvolte šipku, která se zobrazí na pravé straně webové části, a zvolte možnost **Zobrazit správce pouze** z nabídky, která se zobrazí.

     Ve webové části se zobrazí pouze zaměstnanci, kteří jsou správci.

2. Zvolte šipku znovu a pak zvolte možnost **Zobrazit všechny zaměstnance** z nabídky, která se zobrazí.

     Všichni zaměstnanci se zobrazí ve webové části.

## <a name="see-also"></a>Viz také

[Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Postupy: Vytvoření webové části](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 služby SharePoint [Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
