---
title: 'Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90da255beb0a85a302158feb1f9d5cc4981437eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520131"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook
  Můžou nastat situace, kdy nechcete, aby aplikace systém Microsoft Office Outlook zobrazovala oblast formuláře pro konkrétní položku. Pokud například položka kontaktu neobsahuje obchodní adresu, můžete zabránit oblasti formuláře, která zobrazuje umístění firmy na mapě.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Zabránění zobrazení oblasti formuláře v aplikaci Outlook

1. Otevřete soubor kódu pro oblast formuláře, kterou chcete upravit.

2. Rozbalte oblast kód pro **vytváření oblasti formuláře** .

3. Přidejte kód do `FormRegionInitializing` obslužné rutiny události, která nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> třídy na **hodnotu true**.

   Pokud v tomto příkladu položka kontaktu neobsahuje adresu, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost je nastavena na **hodnotu true**a oblast formuláře se nezobrazí.

## <a name="example"></a>Příklad
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Viz také
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
