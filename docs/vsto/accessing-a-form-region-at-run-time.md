---
title: Přístup k oblasti formuláře v době běhu
description: Naučte se, jak získat přístup k oblasti formuláře v různých typech projektů a verzích systém Microsoft Office v době běhu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbd60f5773392af2066e4693751dd6fff99128b9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827965"
---
# <a name="access-a-form-region-at-run-time"></a>Přístup k oblasti formuláře v době běhu

|Platí pro|
|----------------|
|Informace v tomto tématu se vztahují pouze na následující typy projektů a verze systému Microsoft Office. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> – Projekty doplňku VSTO<br /><br /> **Verze systém Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Použijte `Globals` třídu pro přístup k oblastem formuláře odkudkoli v rámci projektu aplikace Outlook. Další informace o `Globals` třídě naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Přístup k oblastem formuláře, které se zobrazují v konkrétním okně kontroly Outlooku
 Chcete-li získat přístup ke všem oblastem formuláře, které se zobrazí v určitém inspektoru aplikace Outlook, zavolejte `FormRegions` vlastnost `Globals` třídy a předejte <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který představuje inspektor.

 Následující příklad získá kolekci oblastí formuláře, které se zobrazí v inspektoru, který aktuálně má fokus. Tento příklad pak přistupuje k oblasti formuláře v kolekci s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet2":::

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Přístup k oblastem formuláře, které se zobrazují v konkrétním okně Průzkumníka Outlooku
 Chcete-li získat přístup ke všem oblastem formuláře, které se zobrazí v konkrétní aplikaci Outlook Explorer, zavolejte `FormRegions` vlastnost `Globals` třídy a předejte <xref:Microsoft.Office.Interop.Outlook.Explorer> objekt, který představuje Průzkumníka.

 Následující příklad získá kolekci oblastí formuláře, které se zobrazí v Průzkumníkovi, který aktuálně má fokus. Tento příklad pak přistupuje k oblasti formuláře v kolekci s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet3":::

## <a name="access-all-form-regions"></a>Přístup ke všem oblastem formuláře
 Chcete-li získat přístup ke všem oblastem formuláře, které se zobrazí ve všech prohlížečích a všech kontrolorech, zavolejte `FormRegions` vlastnost `Globals` třídy.

 Následující příklad získá kolekci oblastí formuláře, které se zobrazí ve všech prohlížečích a všech kontrolách. Tento příklad pak přistupuje k oblasti formuláře s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet1":::

## <a name="access-controls-on-a-form-region"></a>Řízení přístupu v oblasti formuláře
 Chcete-li získat přístup k ovládacím prvkům v oblasti formuláře pomocí `Globals` třídy, je nutné nastavit ovládací prvky jako přístupné pro kód mimo soubor kódu oblasti formuláře.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Oblasti formulářů navržené v Návrháři oblasti formuláře
 V jazyce C# změňte modifikátor každého ovládacího prvku, ke kterému chcete získat přístup. Provedete to tak, že vyberete všechny ovládací prvky v Návrháři oblastí formuláře a v okně **vlastnosti** změníte vlastnost **modifikátory** na **interní** nebo **veřejný** . Například pokud změníte vlastnost **modifikátoru** `textBox1` na **interní**, získáte přístup `textBox1` zadáním `Globals.FormRegions.FormRegion1.textBox1` .

 Pro Visual Basic nemusíte měnit modifikátor.

### <a name="imported-form-regions"></a>Importované oblasti formuláře
 Při importu oblasti formuláře navržené v aplikaci Outlook se modifikátor přístupu každého ovládacího prvku v oblasti formuláře nastaví jako soukromý. Vzhledem k tomu, že nemůžete použít Návrhář oblasti formuláře pro úpravu importované oblasti formuláře, neexistuje žádný způsob, jak změnit modifikátor ovládacího prvku v okně **vlastnosti** .

 Chcete-li povolit přístup k ovládacímu prvku mimo soubor kódu oblasti formuláře, vytvořte v souboru kódu oblasti formuláře vlastnost, která tento ovládací prvek vrátí.

 Další informace o tom, jak vytvořit vlastnosti v jazyce C#, naleznete v tématu [How to: Declare and use Read Write properties &#40;C&#35; Programming guide&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Další informace o tom, jak vytvořit vlastnosti v Visual Basic, naleznete v tématu [How to: Create a Property (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Viz také
- [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
