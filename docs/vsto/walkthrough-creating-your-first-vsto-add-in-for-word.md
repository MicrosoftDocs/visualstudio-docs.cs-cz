---
title: 'Návod: vytvoření prvního doplňku VSTO pro Word'
description: Vytvoření doplňku na úrovni aplikace pro aplikaci Microsoft Word Tato funkce je k dispozici pro samotnou aplikaci, bez ohledu na to, které dokumenty jsou otevřené.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc136b1c58f9c627787045b1259d07e27a6b8ad
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527873"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Návod: vytvoření prvního doplňku VSTO pro Word
  V tomto úvodním návodu se dozvíte, jak vytvořit doplněk VSTO pro systém Microsoft Office Word. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pro samotnou aplikaci, bez ohledu na to, které dokumenty jsou otevřené.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu doplňku VSTO pro Word

- Psaní kódu, který používá objektový model aplikace Word k přidání textu do dokumentu, když je uložen.

- Sestavení a spuštění projektu pro otestování.

- Vyčistěte dokončený projekt, aby se tento doplněk VSTO na vývojovém počítači nespouštěl automaticky.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Vytvoření projektu

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Vytvoření nového projektu doplňku VSTO pro Word v aplikaci Visual Studio

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic** a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **Doplňky Office** .

5. V seznamu šablon projektu vyberte projekt doplňku VSTO aplikace Word.

6. Do pole **název** zadejte **FirstWordAddIn**.

7. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt **FirstWordAddIn** a otevře soubor s kódem ThisAddIn v editoru.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Napsání kódu pro přidání textu do uloženého dokumentu
 Dále přidejte kód do souboru kódu ThisAddIn. Nový kód používá objektový model aplikace Word k přidání často používaného textu do každého uloženého dokumentu. Ve výchozím nastavení soubor kódu ThisAddIn obsahuje následující generovaný kód:

- Částečná definice `ThisAddIn` třídy. Tato třída poskytuje vstupní bod pro váš kód a poskytuje přístup k objektovému modelu aplikace Word. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md). Zbytek `ThisAddIn` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Obslužné rutiny události a. Tyto obslužné rutiny události jsou volány, když aplikace Word načte a uvolní doplněk VSTO. Tyto obslužné rutiny událostí použijte k inicializaci doplňku VSTO po jeho načtení a k vyčištění prostředků používaných doplňkem VSTO, když se uvolní. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Přidání odstavce textu do uloženého dokumentu

1. V souboru kódu ThisAddIn přidejte do třídy následující kód `ThisAddIn` . Nový kód definuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událost, která je vyvolána při uložení dokumentu.

    Když uživatel dokument uloží, obslužná rutina události přidá nový text na začátku dokumentu.

    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]

   > [!NOTE]
   > Tento kód používá hodnotu indexu 1 pro přístup k prvnímu odstavci v <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> kolekci. I když Visual Basic a Visual C# používají pole na bázi 0, dolní hranice pole většiny kolekcí v objektovém modelu aplikace Word je 1. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).

2. Pokud používáte jazyk C#, přidejte následující požadovaný kód do `ThisAddIn_Startup` obslužné rutiny události. Tento kód slouží k propojení `Application_DocumentBeforeSave` obslužné rutiny události s <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událostí.

    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]

   Chcete-li upravit dokument při jeho uložení, předchozí příklady kódu používají následující objekty:

- `Application`Pole `ThisAddIn` třídy `Application`Pole vrátí <xref:Microsoft.Office.Interop.Word.Application> objekt, který představuje aktuální instanci aplikace Word.

- `Doc`Parametr obslužné rutiny události <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . `Doc`Parametr je <xref:Microsoft.Office.Interop.Word.Document> objekt, který představuje uložený dokument. Další informace najdete v tématu [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Testování projektu

### <a name="to-test-the-project"></a>Otestování projektu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je součástí výstupní složky sestavení pro projekt. Sada Visual Studio také vytvoří sadu položek registru, které umožní aplikaci Word zjistit a načíst doplněk VSTO a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné doplněk VSTO spustit. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

2. V aplikaci Word uložte aktivní dokument.

3. Ověřte, zda je do dokumentu přidán následující text.

     **Tento text byl přidán pomocí kódu.**

4. Zavřete slovo.

## <a name="clean-up-the-project"></a>Vyčištění projektu
 Po dokončení vývoje projektu odeberte sestavení doplňku VSTO, položky registru a nastavení zabezpečení z vývojového počítače. V opačném případě se doplněk VSTO bude i nadále spouštět pokaždé, když otevřete Word na svém vývojovém počítači.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Vyčištění dokončeného projektu ve vývojovém počítači

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky
 Teď, když jste vytvořili základní doplněk VSTO pro Word, můžete získat další informace o tom, jak vyvíjet doplňky VSTO z těchto témat:

- Obecné úlohy programování, které můžete provádět v Doplňkech VSTO: [programový doplněk VSTO](../vsto/programming-vsto-add-ins.md).

- Úkoly programování, které jsou specifické pro Doplňky aplikace Word VSTO: [řešení aplikace Word](../vsto/word-solutions.md).

- Použití objektového modelu aplikace Word: [Přehled objektového modelu aplikace Word](../vsto/word-object-model-overview.md).

- Přizpůsobení uživatelského rozhraní aplikace Word, například přidáním vlastní karty na pás karet nebo vytvořením vlastního podokna úloh: [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

- Sestavování a ladění doplňků VSTO pro Word: [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

- Nasazují se doplňky VSTO pro Word: [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Řešení pro Word](../vsto/word-solutions.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
