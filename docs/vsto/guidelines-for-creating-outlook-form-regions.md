---
title: Pokyny pro vytváření oblastí formulářů aplikace Outlook
description: Seznamte se s pokyny pro vytváření oblastí formulářů Outlooku, které vám pomůžou optimalizovat oblasti formuláře a vyhnout se potenciálním problémům.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aaf6b96548a9856833fcd1768764ed914da30a07
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848089"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Pokyny pro vytváření oblastí formulářů aplikace Outlook
  Následující informace vám můžou přispět k optimalizaci oblastí formuláře a vyhnout se potenciálním problémům:

- [Použijte názvy oblastí formuláře](#UsingFormRegions).

- [Zakáže dědění oblasti formuláře](#DisablingInheritance).

- [Pochopení typů a názvů tříd zpráv](#ClassNames).

- [Navrhněte oblasti sousedících formulářů pro podokno čtení](#ReadingPane).

- [Používejte optimální velikosti ikon](#UsingOptimal).

  Další informace o oblastech formuláře najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Použít názvy oblastí formuláře
 K popisu oblasti formuláře se používá několik názvů. Je důležité pochopit rozdíl mezi těmito názvy a jejich vlivem na oblast formuláře. Jednotlivé názvy jsou popsány v následující tabulce.

|Název oblasti formuláře|Popis|
|----------------------|-----------------|
|Název položky oblasti formuláře|Název, který zadáte pro položku **oblast formuláře Outlooku** v dialogovém okně **Přidat novou položku** . Toto je název souboru kódu oblasti formuláře, který se zobrazí v **Průzkumník řešení**.|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> majetek|Tento název zadáte do **popisného textu pro zadání a vyberete stránku předvolby zobrazení** v Průvodci vytvořením **nové oblasti formuláře Outlooku** . Tento název se zobrazí jako vlastnost **FormRegionName** v okně **vlastnosti** .<br /><br /> Vlastnost použijte <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> k určení popisku, který identifikuje oblast formuláře v uživatelském rozhraní aplikace Outlook (UI). U samostatných oblastí formuláře se tento název zobrazí jako tlačítko na pásu karet položky Outlooku.<br /><br /> V případě sousedících oblastí formuláře se tento název zobrazuje jako text záhlaví nad oblastí formuláře.|
|Atribut `Microsoft.Office.Tools.Outlook.FormRegionName`|Když do projektu přidáte položku **oblasti formuláře aplikace Outlook** , sada Visual Studio nastaví tuto vlastnost na plně kvalifikovaný název oblasti formuláře. Výchozí plně kvalifikovaný název je název doplňku VSTO připojeného k názvu oblasti formuláře tečkou, například `OutlookAddIn1.FormRegion1` .<br /><br /> Tento plně kvalifikovaný název se zobrazí také jako atribut v horní části třídy Factory oblasti formuláře.<br /><br /> Pomocí `Microsoft.Office.Tools.Outlook.FormRegionName` atributu můžete jedinečně identifikovat oblast formuláře napříč všemi doplňky VSTO pro Outlook. Hodnotu atributu nelze změnit `Microsoft.Office.Tools.Outlook.FormRegionName` přejmenováním položky oblasti formuláře nebo změnou <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Vlastnosti. Chcete-li změnit tento název, je nutné upravit `Microsoft.Office.Tools.Outlook.FormRegionName` atribut v souboru kódu oblasti formuláře.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Zakázat dědičnost oblastí formuláře
 Ve výchozím nastavení zdědí vlastní třída Message přidružení všech oblastí formuláře základní třídy zpráv. Například třída zpráv s názvem `IPM.Task.Contoso` je odvozena z `IPM.Task` . Proto `IPM.Task.Contoso` dědí přidružení oblasti formuláře pro `IPM.Task` .

 Pokud nechcete, aby oblast formuláře byla přidružena k žádným odvozeným třídám zpráv, nastavte <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> vlastnost oblasti formuláře na **hodnotu true**. Pokud například přidružíte sousední oblast formuláře k `IPM.Task` a nastavíte <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> vlastnost na **hodnotu true**, oblast formuláře se připojí pouze k dolnímu okraji formuláře standardní úlohy. Oblast formuláře nebude připojena k dolnímu okraji všech přizpůsobených verzí formuláře standardní úlohy.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Pochopení typů a názvů tříd zpráv
 Název typu položky aplikace Outlook se liší od názvu třídy zprávy položky Outlook. Například název typu položky RSS je `Microsoft.Office.Interop.Outlook.PostItem` . Název třídy zprávy položky RSS je `IPM.Post.RSS` .

 Použijte název typu pro odkazování na položku Outlooku v kódu. Seznam názvů typů naleznete v tématu [přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Chcete-li přidružit položku k oblasti formuláře, použijte název třídy zprávy položky Outlook v Průvodci vytvořením **oblasti formuláře Outlooku** . Seznam platných názvů tříd zpráv naleznete v tématu [přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Návrh sousedících oblastí formuláře pro podokno čtení
 Můžete použít podokno čtení aplikace Outlook k zobrazení náhledu položky aplikace Outlook bez otevření položky. Podokno pro čtení je určené pouze pro čtení. Proto vstupní ovládací prvky, které přidáte do sousední oblasti formuláře, jako je například textové pole, se nemusí chovat podle očekávání, pokud je oblast položka a formulář otevřená v podokně pro čtení.

 Například pokud je položka, která má oblast sousedícího formuláře, otevřená v podokně pro čtení, je možné použít následující situaci:

1. Vyberte nějaký text v textovém poli, které je v oblasti formuláře.

2. Stiskněte klávesu **Delete**.

3. Místo textu v textovém poli se odstraní celá položka pošty.

   Pokud navrhujete sousedící oblast formuláře, která obsahuje vstupní ovládací prvky, otestujte ovládací prvky v podokně pro čtení a ujistěte se, že fungují správně. Zvažte přidání vlastního kódu, který zakáže ovládací prvky, které se nechovají podle očekávání.

   Případně můžete nastavit <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> vlastnost oblasti formuláře na **hodnotu NEPRAVDA**. Tímto způsobem nelze použít oblast formuláře v podokně pro čtení.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> Použít optimální velikosti ikon
 Můžete určit, které ikony má oblast formuláře zobrazit, nastavením vlastností ikony ve skupině vlastností **ikony** v okně **vlastnosti** . Pomocí následujících pokynů můžete dosáhnout nejlepší vizuální kvality:

- Pro ikonu **stránky** použijte soubor PNG (Portable Network Graphics).

- Ikony **okna** by měly být 32 × 32 pixelů.

- Všechny ostatní ikony by měly být 16 × 16 pixelů.

  Ikona **stránky** se zobrazí na pásu karet inspektora pro položky, které mají samostatné, nahrazující nebo nahrazené oblasti formuláře.

  Ikona **okna** se zobrazí v oznamovací oblasti a v **Alt** + dialogovém okně **karta** Alt pro otevřené položky, které zobrazují náhradní nebo nahrazené oblasti formuláře.

## <a name="see-also"></a>Viz také
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
