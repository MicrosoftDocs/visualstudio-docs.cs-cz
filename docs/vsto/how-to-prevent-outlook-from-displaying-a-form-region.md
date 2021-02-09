---
title: 'Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook'
description: Přečtěte si, jak můžete zabránit aplikaci systém Microsoft Office Outlook v zobrazování oblasti formuláře pro konkrétní položku.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f6e6b00e8e26d261aac18dd48af1d912bd6ffad1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899553"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Postupy: zabránění zobrazení oblasti formuláře v aplikaci Outlook
  Můžou nastat situace, kdy nechcete, aby aplikace systém Microsoft Office Outlook zobrazovala oblast formuláře pro konkrétní položku. Pokud například položka kontaktu neobsahuje obchodní adresu, můžete zabránit oblasti formuláře, která zobrazuje umístění firmy na mapě.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Zabránění zobrazení oblasti formuláře v aplikaci Outlook

1. Otevřete soubor kódu pro oblast formuláře, kterou chcete upravit.

2. Rozbalte oblast kód pro **vytváření oblasti formuláře** .

3. Přidejte kód do `FormRegionInitializing` obslužné rutiny události, která nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> třídy na **hodnotu true**.

   Pokud v tomto příkladu položka kontaktu neobsahuje adresu, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost je nastavena na **hodnotu true** a oblast formuláře se nezobrazí.

## <a name="example"></a>Příklad
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Viz také
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
