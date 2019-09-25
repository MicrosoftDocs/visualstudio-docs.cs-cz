---
title: Přístup k oblasti formuláře v době běhu
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5dd8818b57a1aa33b70254303150d8f00e36cc02
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255802"
---
# <a name="access-a-form-region-at-run-time"></a>Přístup k oblasti formuláře v době běhu

|Platí pro|
|----------------|
|Informace v tomto tématu se vztahují pouze na následující typy projektů a verze systému Microsoft Office. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> – Projekty doplňku VSTO<br /><br /> **Verze systém Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 `Globals` Použijte třídu pro přístup k oblastem formuláře odkudkoli v rámci projektu aplikace Outlook. Další informace o `Globals` třídě naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Přístup k oblastem formuláře, které se zobrazují v konkrétním okně kontroly Outlooku
 Chcete-li získat přístup ke všem oblastem formuláře, které se zobrazí v `FormRegions` určitém inspektoru aplikace Outlook, zavolejte <xref:Microsoft.Office.Interop.Outlook.Inspector> vlastnost `Globals` třídy a předejte objekt, který představuje inspektor.

 Následující příklad získá kolekci oblastí formuláře, které se zobrazí v inspektoru, který aktuálně má fokus. Tento příklad pak přistupuje k oblasti formuláře v kolekci s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na. `Hello World`

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Přístup k oblastem formuláře, které se zobrazují v konkrétním okně Průzkumníka Outlooku
 Chcete-li získat přístup ke všem oblastem formuláře, které se zobrazí v `FormRegions` konkrétní aplikaci Outlook `Globals` Explorer, zavolejte vlastnost <xref:Microsoft.Office.Interop.Outlook.Explorer> třídy a předejte objekt, který představuje Průzkumníka.

 Následující příklad získá kolekci oblastí formuláře, které se zobrazí v Průzkumníkovi, který aktuálně má fokus. Tento příklad pak přistupuje k oblasti formuláře v kolekci s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na. `Hello World`

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>Přístup ke všem oblastem formuláře
 Chcete-li získat přístup ke všem oblastem formuláře, které se zobrazí ve všech prohlížečích `FormRegions` a všech kontrolorech, zavolejte vlastnost `Globals` třídy.

 Následující příklad získá kolekci oblastí formuláře, které se zobrazí ve všech prohlížečích a všech kontrolách. Tento příklad pak přistupuje k oblasti formuláře s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>Řízení přístupu v oblasti formuláře
 Chcete-li získat přístup k ovládacím prvkům v `Globals` oblasti formuláře pomocí třídy, je nutné nastavit ovládací prvky jako přístupné pro kód mimo soubor kódu oblasti formuláře.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Oblasti formulářů navržené v Návrháři oblasti formuláře
 Pro C#změňte modifikátor každého ovládacího prvku, ke kterému chcete získat přístup. Provedete to tak, že vyberete všechny ovládací prvky v Návrháři oblastí formuláře a v okně **vlastnosti** změníte vlastnost **modifikátory** na **interní** nebo **veřejný** . Například pokud změníte vlastnost `textBox1` **modifikátoru** na **interní**, získáte přístup `textBox1` zadáním. `Globals.FormRegions.FormRegion1.textBox1`

 Pro Visual Basic nemusíte měnit modifikátor.

### <a name="imported-form-regions"></a>Importované oblasti formuláře
 Při importu oblasti formuláře navržené v aplikaci Outlook se modifikátor přístupu každého ovládacího prvku v oblasti formuláře nastaví jako soukromý. Vzhledem k tomu, že nemůžete použít Návrhář oblasti formuláře pro úpravu importované oblasti formuláře, neexistuje žádný způsob, jak změnit modifikátor ovládacího prvku v okně **vlastnosti** .

 Chcete-li povolit přístup k ovládacímu prvku mimo soubor kódu oblasti formuláře, vytvořte v souboru kódu oblasti formuláře vlastnost, která tento ovládací prvek vrátí.

 Další informace o tom, jak vytvořit vlastnosti v C#nástroji, [naleznete v tématu How to: Deklarujte &#40;a použijte průvodce&#35; &#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties)pro čtení a zápis vlastností.

 Další informace o tom, jak vytvořit vlastnosti v Visual Basic, najdete [v tématu How to: Vytvořte vlastnost (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Viz také:
- [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku pro Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Návod: Import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Postupy: Zabránit zobrazení oblasti formuláře v aplikaci Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
