---
title: Přidružení oblasti formuláře k třídě zpráv aplikace Outlook
description: Zjistěte, jak můžete určit, které systém Microsoft Office položky Outlooku budou zobrazovat oblast formuláře, a to přidružením oblasti formuláře k třídě zpráv každé položky.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be3b789fabf00d853d447cb3489ef07a5b494fcd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826990"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Přidružení oblasti formuláře k třídě zpráv aplikace Outlook
  Můžete určit, které systém Microsoft Office položky Outlooku zobrazit oblast formuláře přidružením oblasti formuláře k třídě zpráv každé položky. Například pokud chcete připojit oblast formuláře k dolní části položky pošty, můžete přidružit oblast formuláře ke `IPM.Note` třídě zprávy.

 Chcete-li přidružit oblast formuláře ke třídě zprávy, zadejte název třídy zprávy v Průvodci vytvořením **nové oblasti formuláře aplikace Outlook** nebo použijte atribut pro třídu factory oblasti formuláře.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Principy tříd zpráv Outlooku
 Třída zprávy Outlook identifikuje typ položky Outlooku. Následující tabulka uvádí tyto osm standardních typů položek a jejich názvy tříd zpráv.

|Typ položky Outlooku|Název třídy zprávy|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` nebo `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Můžete také zadat názvy vlastních tříd zpráv. Vlastní třídy zpráv identifikují vlastní formuláře, které definujete v aplikaci Outlook.

> [!NOTE]
> V případě nahrazení a nahrazení – všechny oblasti formulářů můžete zadat nový název vlastní třídy zpráv. Nemusíte používat název třídy zprávy existujícího vlastního formuláře. Název vlastní třídy zpráv musí být jedinečný. Jedním ze způsobů, jak zajistit, aby byl název jedinečný, je použít konvenci pojmenování podobnou následující: \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (například: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Přidružení oblasti formuláře k třídě zpráv aplikace Outlook
 Existují dva způsoby, jak přidružit oblast formuláře ke třídě zprávy:

- Použijte průvodce **vytvořením nové oblasti formuláře Outlooku** .

- Použijte atributy třídy.

### <a name="use-the-new-outlook-form-region-wizard"></a>Použití Průvodce novou oblastí formuláře Outlooku
 Na poslední stránce Průvodce vytvořením **oblasti formuláře Outlooku** můžete vybrat standardní třídy zpráv a zadat názvy vlastních tříd zpráv, které chcete přidružit k oblasti formuláře.

 Standardní třídy zpráv nejsou k dispozici, pokud je oblast formuláře navržena tak, aby nahradila celý formulář nebo výchozí stránku formuláře. Standardní názvy tříd zpráv lze zadat pouze pro formuláře, které přidají novou stránku do formuláře nebo které jsou připojeny k dolnímu okraji formuláře. Další informace najdete v tématu [Postup: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Chcete-li zahrnout jednu nebo více vlastních tříd zpráv, zadejte jejich názvy do polí, **které vlastní třídy zpráv zobrazí tuto oblast formuláře?** .

 Názvy, které zadáte, musí splňovat následující pokyny:

- Použijte plně kvalifikovaný název třídy zprávy (například: "IPM". Poznámka. contoso ").

- K oddělení více názvů tříd zpráv použijte středníky.

- Nezahrnujte standardní třídy zpráv Outlooku, například "IPM". Poznámka "nebo" IPM. Kontaktujte ". Zahrnout pouze vlastní třídy zpráv, například "IPM. Poznámka. contoso.

- Nezadávejte třídu základní zprávy samostatně (například: "IPM").

- Pro každý název třídy zprávy nesmí překročit 256 znaků.

  Průvodce **novou oblastí formuláře aplikace Outlook** ověří formát vstupu po kliknutí na tlačítko **Dokončit**.

> [!NOTE]
> Průvodce **novou oblastí formuláře Outlooku** neověřuje, jestli jsou názvy tříd zpráv, které zadáte, správné nebo platné.

 Po dokončení průvodce se v novém průvodci **oblastí formuláře Outlooku** použijí atributy pro třídu region formuláře, která obsahuje zadané názvy tříd zpráv. Tyto atributy můžete použít také ručně.

### <a name="apply-class-attributes"></a>Použít atributy třídy
 Po dokončení Průvodce vytvořením **nové oblasti formuláře Outlooku** můžete přiřadit oblast formuláře k třídě zpráv aplikace Outlook. K tomu použijte atributy pro třídu factory oblasti formuláře.

 Následující příklad ukazuje dva <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atributy, které byly aplikovány na třídu objektu pro vytváření oblasti formuláře s názvem `myFormRegion` . První atribut přidružuje oblast formuláře ke standardní třídě zprávy pro formulář poštovní zprávy. Druhý atribut přidruží oblast formuláře k vlastní třídě zpráv s názvem `IPM.Task.Contoso` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs" id="Snippet1":::

 Atributy musí splňovat následující pokyny:

- Pro vlastní třídy zpráv použijte plně kvalifikovaný název třídy zprávy (například: "IPM". Poznámka. contoso ").

- Nezadávejte třídu základní zprávy samostatně (například: "IPM").

- Pro každý název třídy zprávy nesmí překročit 256 znaků.

- Nezahrnujte názvy standardních tříd zpráv, pokud oblast formuláře nahradí celý formulář nebo výchozí stránku formuláře. Standardní názvy tříd zpráv lze zadat pouze pro formuláře, které přidají novou stránku do formuláře nebo které jsou připojeny k dolnímu okraji formuláře. Další informace najdete v tématu [Postup: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Při sestavování projektu ověří aplikace Visual Studio formát názvů tříd zpráv.

> [!NOTE]
> Visual Studio neověřuje, jestli jsou názvy tříd zpráv, které zadáte, správné nebo platné.

## <a name="see-also"></a>Viz také
- [Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Název formuláře a třída zpráv – přehled](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Jak spolupracují formuláře a položky aplikace Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
