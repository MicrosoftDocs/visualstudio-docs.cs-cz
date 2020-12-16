---
title: 'Návod: vytvoření prvního doplňku VSTO pro PowerPoint'
description: Vytvoření doplňku na úrovni aplikace pro aplikaci Microsoft PowerPoint Tato funkce je k dispozici pro samotnou aplikaci, bez ohledu na to, jaké prezentace jsou otevřené.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e02da3484ce7c2beb35e643d3d90d8e37225e11
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524849"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Návod: vytvoření prvního doplňku VSTO pro PowerPoint
  V tomto návodu se dozvíte, jak vytvořit doplněk VSTO pro systém Microsoft Office PowerPointu. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pro samotnou aplikaci, bez ohledu na to, jaké prezentace jsou otevřené. Další informace najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu doplňku VSTO pro PowerPoint pro PowerPoint

- Psaní kódu, který používá objektový model aplikace PowerPoint k přidání textového pole do každého nového snímku.

- Sestavení a spuštění projektu pro otestování.

- Vyčistěte projekt, aby se doplněk VSTO na vašem vývojovém počítači už nespouštěl automaticky.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Vytvoření projektu

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic** a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **Doplňky Office** .

5. V seznamu šablon projektu vyberte projekt doplňku VSTO pro PowerPoint.

6. Do pole **název** zadejte **FirstPowerPointAddIn**.

7. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt **FirstPowerPointAddIn** a otevře soubor s kódem **ThisAddIn** v editoru.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Napsat kód, který do každého nového snímku přidá text
 Dále přidejte kód do souboru kódu ThisAddIn. Nový kód používá objektový model aplikace PowerPoint k přidání textového pole do každého nového snímku. Ve výchozím nastavení soubor kódu ThisAddIn obsahuje následující generovaný kód:

- Částečná definice `ThisAddIn` třídy. Tato třída poskytuje vstupní bod pro váš kód a poskytuje přístup k objektovému modelu aplikace PowerPoint. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md). Zbytek `ThisAddIn` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Obslužné rutiny události a. Tyto obslužné rutiny události jsou volány, když aplikace PowerPoint načte a uvolní doplněk VSTO. Tyto obslužné rutiny událostí použijte k inicializaci doplňku VSTO po jeho načtení a k vyčištění prostředků používaných doplňkem VSTO, když se uvolní. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-text-box-to-each-new-slide"></a>Přidání textového pole do každého nového snímku

1. V souboru kódu ThisAddIn přidejte do třídy následující kód `ThisAddIn` . Tento kód definuje obslužnou rutinu události pro událost [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) objektu [Application](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) .

    Když uživatel přidá nový snímek do aktivní prezentace, přidá tato obslužná rutina události do horní části nového snímku textové pole a přidá do textového pole nějaký text.

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. Pokud používáte jazyk C#, přidejte následující kód do `ThisAddIn_Startup` obslužné rutiny události. Tento kód je vyžadován pro připojení `Application_PresentationNewSlide` obslužné rutiny události [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) .

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   Pro úpravu každého nového snímku používají předchozí příklady kódu následující objekty:

- `Application`Pole `ThisAddIn` třídy `Application`Pole vrátí objekt [aplikace](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) , který představuje aktuální instanci aplikace PowerPoint.

- `Sld`Parametr obslužné rutiny události [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) `Sld`Parametr je objekt [snímku](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) , který představuje nový snímek. Další informace najdete v tématu [řešení pro PowerPoint](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Testování projektu
 Při sestavování a spouštění projektu ověřte, zda se textové pole zobrazuje v nových snímcích, které přidáte do prezentace.

### <a name="to-test-the-project"></a>Otestování projektu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je vloženo do výstupní složky sestavení pro projekt. Sada Visual Studio také vytvoří sadu položek registru, které umožní aplikaci PowerPoint vyhledat a načíst doplněk VSTO a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné doplněk VSTO spustit. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

2. V aplikaci PowerPoint přidejte do aktivní prezentace nový snímek.

3. Ověřte, zda je do nového textového pole v horní části snímku přidáno následující text.

     **Tento text byl přidán pomocí kódu.**

4. Zavřete PowerPoint.

## <a name="clean-up-the-project"></a>Vyčištění projektu
 Po dokončení vývoje projektu odeberte sestavení doplňku VSTO, položky registru a nastavení zabezpečení z vývojového počítače. V opačném případě se doplněk VSTO spustí pokaždé, když ve vývojovém počítači otevřete PowerPoint.

### <a name="to-clean-up-your-project"></a>Vyčištění projektu

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky
 Teď, když jste vytvořili základní doplněk VSTO pro PowerPoint, můžete získat další informace o tom, jak vyvíjet doplňky VSTO z těchto témat:

- Obecné úlohy programování, které můžete provádět v Doplňkech VSTO pro PowerPoint Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

- Pomocí objektového modelu aplikace PowerPoint. Další informace najdete v tématu [řešení pro PowerPoint](../vsto/powerpoint-solutions.md).

- Přizpůsobení uživatelského rozhraní aplikace PowerPoint, například přidáním vlastní karty na pás karet nebo vytvořením vlastního podokna úloh. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

- Sestavování a ladění doplňků VSTO pro PowerPoint Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

- Nasazují se doplňky VSTO pro PowerPoint. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Řešení aplikace PowerPoint](../vsto/powerpoint-solutions.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
