---
title: 'Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook'
description: Naučte se, jak vytvořit oblast formuláře pro rozšiřování standardního nebo vlastního systém Microsoft Office formuláře Outlooku pomocí Průvodce vytvořením nové oblasti formuláře Outlooku.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f50475f52ca2ec08894a3c1c0375e78d2b5620b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917531"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook
  Vytvořte oblast formuláře pro rozšiřování standardního nebo vlastního systém Microsoft Officeho formuláře Outlooku pomocí Průvodce vytvořením **nové oblasti formuláře Outlooku** . Můžete vytvořit novou oblast formuláře a navrhnout uživatelské rozhraní v aplikaci Visual Studio nebo můžete importovat oblast formuláře, která byla navržena v aplikaci Outlook a přidat Visual Basic nebo kód jazyka C#.

 Pokud máte oblast formuláře Outlooku, kterou jste použili v jiném projektu Outlooku, můžete ji znovu použít v aktuálním projektu doplňku VSTO pro Outlook pomocí dialogového okna **Přidat existující položku** . Další informace najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Přidání nové oblasti formuláře do projektu aplikace Outlook

1. Otevřete nebo vytvořte projekt doplňku VSTO pro Outlook v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. V **Průzkumník řešení** vyberte uzel projektu DOPLŇKu VSTO pro Outlook.

3. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

4. V dialogovém okně **Přidat novou položku** vyberte možnost **oblast formuláře aplikace Outlook**.

5. Do pole **název** zadejte název oblasti formuláře a pak klikněte na **Přidat**.

     Spustí se průvodce **oblastí formuláře NewOutlook** .

6. Na stránce **Vyberte, jak chcete vytvořit oblast formuláře** , vyberte, zda chcete navrhnout oblast formuláře přetažením spravovaných ovládacích prvků do vizuálního návrháře nebo importovat oblast formuláře, která byla navržena v aplikaci Outlook.

    > [!NOTE]
    > Pokud se rozhodnete importovat oblast formuláře, která byla navržena v aplikaci Outlook, je nutné zadat umístění souboru úložiště formuláře aplikace Outlook (*. ofs*). Do oblasti formuláře, kterou navrhujete v aplikaci Outlook, nelze přidat spravované ovládací prvky. můžete přidat jenom kód za stávajícím uživatelským rozhraním. Další informace najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

7. Na stránce **Vyberte typ oblasti formuláře, kterou chcete vytvořit** , zkontrolujte typy oblastí formuláře a vyberte jednu a potom klikněte na tlačítko **Další**. Další informace o typech oblastí formuláře najdete v tématu věnovaném [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

8. V poli název zadejte **popisný text a vyberte stránku předvolby zobrazení** , do pole **název** zadejte název oblasti formuláře. V případě nahrazení a nahrazení-všechny typy oblastí formuláře jsou k dispozici také pole **název** a **Popis** .

     Informace o tom, kde se název, název a popis zobrazí v aplikaci Outlook při nasazení oblasti formuláře, najdete v tématu věnovaném [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

9. Vyberte jeden nebo více režimů zobrazení, ve kterých chcete zobrazit oblast formuláře.

     Všechny typy oblastí formuláře se mohou objevit v okně kontroly v režimu psaní (pro vytváření položek) a v režimu čtení (pro zobrazení položek). Sousedící, nahrazování a nahrazování – všechny typy oblastí formuláře se mohou zobrazit také v podokně pro čtení.

10. Klikněte na **Next** (Další).

11. V části **Určete třídy zpráv, které budou zobrazovat tuto stránku oblasti formuláře** , vyberte standardní třídy zpráv aplikace Outlook nebo zadejte názvy jedné nebo více vlastních tříd zpráv a potom klikněte na tlačítko **Dokončit**. Další informace naleznete v tématu [přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Viz také
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
- [Řešení pro Outlook](../vsto/outlook-solutions.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Návod: import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
