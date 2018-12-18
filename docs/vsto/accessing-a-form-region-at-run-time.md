---
title: Přístup k oblasti formuláře za běhu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f2c1f3e80f5ca4015a19b5eee7f2f4c673dcc615
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304477"
---
# <a name="access-a-form-region-at-runtime"></a>Přístup k oblasti formuláře za běhu

|Platí pro|  
|----------------|  
|Informace v tomto tématu se vztahují jenom na tyto typy projektů a verze Microsoft Office. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> -Projekty doplňků VSTO<br /><br /> **Verze aplikace Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Použití `Globals` třídy pro oblasti formuláře přístup z libovolného místa v rámci projektu aplikace Outlook. Další informace o `Globals` najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Přístup k oblasti formuláře, které se zobrazí v okně konkrétní aplikace Outlook inspektoru  
 Pro přístup k všechny oblasti formuláře, které se zobrazují v konkrétní Kontrola aplikace Outlook, volejte `FormRegions` vlastnost `Globals` třídy a předejte mu <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který reprezentuje inspektor.  

 Následující příklad získá kolekci oblastí formulářů, které se zobrazí v okně Inspektor, který má aktuálně fokus. Tento příklad následně přistupuje k oblasti formuláře v kolekci s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Přístup k oblasti formuláře, které se zobrazují v konkrétní okno Průzkumníka aplikace Outlook  
 Pro přístup k všechny oblasti formuláře, které se zobrazují v konkrétní Průzkumníku aplikace Outlook, volejte `FormRegions` vlastnost `Globals` třídy a předejte mu <xref:Microsoft.Office.Interop.Outlook.Explorer> objekt, který reprezentuje Průzkumníka.  

 Následující příklad získá kolekci oblastí formulářů, které se zobrazí v Průzkumníkovi, který má aktuálně fokus. Tento příklad následně přistupuje k oblasti formuláře v kolekci s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="access-all-form-regions"></a>Všechny oblasti formulářů  
 Chcete-li získat přístup k všechny oblasti formuláře, které se zobrazují všechny Průzkumníci a všechny kontroly, zavolejte `FormRegions` vlastnost `Globals` třídy.  

 Následující příklad získá kolekci oblastí formulářů, které se zobrazují všechny Průzkumníci a všechny kontroly. Tento příklad následně přistupuje k oblasti formuláře s názvem `formRegion1` a nastaví text, který se zobrazí v textovém poli na `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="access-controls-on-a-form-region"></a>Řízení přístupu na oblast formuláře  
 K řízení přístupu na oblast formuláře pomocí `Globals` třídy, je třeba ovládací prvky přístupné pro kód mimo kódu soubor oblasti formuláře.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Oblasti formuláře navržené v návrhářem oblasti formuláře  
 Pro C#, změňte modifikátor každý ovládací prvek, který chcete získat přístup. Chcete-li to provést, vyberte každý ovládací prvek v Návrháři oblasti formuláře a změňte **modifikátory** vlastnost **interní** nebo **veřejné** v **vlastnosti** okna. Například, pokud změníte **modifikátor** vlastnost `textBox1` k **interní**, dostanete `textBox1` zadáním `Globals.FormRegions.FormRegion1.textBox1`.  

 V jazyce Visual Basic není potřeba změnit modifikátor.  

### <a name="imported-form-regions"></a>Oblasti importované formuláře  
 Při importu oblasti formuláře, která je navržená v Outlooku se stane privátní modifikátor přístupu každého ovládacího prvku na oblast formuláře. Protože návrhářem oblasti formuláře nelze použít k úpravě určitá oblast importované formuláře, neexistuje žádný způsob, jak změnit Modifikátor ovládacího prvku v **vlastnosti** okna.  

 Pokud chcete povolit přístup k ovládacímu prvku z vnějšku souboru, kód oblasti formuláře, vytvoření vlastnosti v souboru kódu oblasti formuláře k vrácení ovládacího prvku.  

 Další informace o tom, jak vytvořit vlastnosti v C#, naleznete v tématu [postupy: deklarování a použití číst, Zapisovat vlastnosti &#40;C&#35; programováním&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Další informace o tom, jak vytvořit vlastnosti v jazyce Visual Basic najdete v tématu [postupy: vytvoření vlastnosti (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Viz také:  
 [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Návod: Importujte oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Postupy: zabránění zobrazení oblasti formuláře Outlooku](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)  
