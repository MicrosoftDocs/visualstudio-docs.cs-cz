---
title: Přidružení oblasti formuláře k třídě zpráv aplikace Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b9614a0feab70dd97cfd64861737c8b42dd146b7
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248030"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Přidružení oblasti formuláře k třídě zpráv aplikace Outlook
  Můžete určit oblast formuláře zobrazit podle přidružení oblasti formuláře k třídě zpráv každé položky, položky, které aplikace Microsoft Office Outlook. Například pokud se chcete připojit k dolnímu okraji položky pošty oblasti formuláře, můžete přidružit oblasti formuláře s `IPM.Note` třída zprávy.  
  
 Přidružení oblasti formuláře s třídou zprávu, zadejte název třídy zpráv v **novou oblast formuláře Outlooku** průvodce nebo použít atribut pro třídu objektů factory oblasti formuláře.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>Pochopení třídy zpráv Outlooku  
 K třídě zpráv aplikace Outlook identifikuje typ položky aplikace Outlook. V následující tabulce jsou uvedeny typy osm standardních položek a jejich názvy tříd zpráv.  
  
|Typ položky aplikace Outlook|Název třídy zpráv|  
|-----------------------|------------------------|  
|Částí AppointmentItem|`IPM.Appointment`|  
|ContactItem|`IPM.Contact`|  
|DistListItem|`IPM.DistList`|  
|JournalItem|`IPM.Activity`|  
|MailItem|`IPM.Note`|  
|PostItem|`IPM.Post` Nebo `IPM.Post.RSS`|  
|TaskItem|`IPM.Task`|  
  
 Můžete také zadat názvy vlastní třídy zpráv. Vlastní třídy zpráv identifikovat vlastních formulářů, které definujete v Outlooku.  
  
> [!NOTE]  
>  Pro nahrazení a nahradit všechno formuláře oblasti můžete zadat nový název třídy vlastní zprávu. Nemusíte použít název třídy zpráv existujícího vlastního formuláře. Název třídy vlastní zprávu musí být jedinečný. Jeden způsob, jak zajistit, že název je jedinečný, je použít zásady vytváření názvů podobný následujícímu: \<*StandardMessageClassName*>.\< *Společnosti*>.\< *MessageClassName*> (například: `IPM.Note.Contoso.MyMessageClass`).  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Přidružení oblasti formuláře k třídě zpráv aplikace Outlook  
 Přidružení oblasti formuláře k třídu zpráv dvěma způsoby:  
  
-   Použití **novou oblast formuláře Outlooku** průvodce.  
  
-   Použití třídy atributů.  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>Pomocí Průvodce novou oblast formuláře Outlooku  
 Na poslední stránce **novou oblast formuláře Outlooku** průvodce, můžete vybrat standardní třídy zpráv a zadejte název vlastní třídy zpráv, které chcete přidružit k oblasti formuláře.  
  
 Standardní třídy zpráv nejsou k dispozici, pokud se oblast formuláře je určena k nahrazení celý formulář nebo výchozí stránku formuláře. Můžete zadat názvy tříd standardní zprávu pouze u formulářů, přidejte novou stránku do formuláře nebo které jsou připojeny k dolní části formuláře. Další informace najdete v tématu [jak: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Chcete-li zahrnout jednu nebo více tříd vlastní zprávu, zadejte jména manažerů v **které vlastní třídy zpráv budou zobrazovat tuto oblast formuláře?** pole.  
  
 Názvy, které zadáte, musí splňovat následující pokyny:  
  
- Použijte název plně kvalifikované třídě (například: "IPM. Note.Contoso").  
  
- K oddělení názvů tříd zpráv více, použijte středníky.  
  
- Nezahrnují standardní třídy zpráv Outlooku, jako je například "IPM. Poznámka:"nebo"IPM. Obraťte se na". Zahrňte pouze vlastní třídy zpráv, jako je například "IPM. Note.Contoso".  
  
- Nezadávejte třída základní zprávy samostatně (například: "PM").  
  
- Není delší než 256 znaků pro každý název třídy zpráv.  
  
  **Novou oblast formuláře Outlooku** Průvodce ověří formát svůj vstup. po kliknutí na **Dokončit**.  
  
> [!NOTE]  
>  **Novou oblast formuláře Outlooku** Průvodce neověřuje, že jsou názvy tříd zpráv, které poskytnete správný nebo platný.  
  
 Po dokončení průvodce **novou oblast formuláře Outlooku** Průvodce použije atributy do třídy oblasti formuláře, která obsahují názvy tříd zadané zprávy. Tyto atributy můžete použít také ručně.  
  
### <a name="apply-class-attributes"></a>Použití třídy atributů  
 Můžete přiřadit oblasti formuláře k třídě zpráv aplikace Outlook po dokončení **novou oblast formuláře Outlooku** průvodce. K tomuto účelu Použíjte atributy do třídy objekt pro vytváření oblasti formuláře.  
  
 Následující příklad ukazuje dva <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atributy, které se použily třídu objekt pro vytváření oblasti formuláře s názvem `myFormRegion`. První atribut přidruží oblasti formuláře s třídou standardní zprávu pro formulář zprávy e-mailu. Druhý atribut přidruží oblasti formuláře k vlastní třídu zpráv s názvem `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Atributy musí splňovat následující pokyny:  
  
- Pro vlastní třídy zpráv, použijte název třídy úplného zprávy (třeba: "IPM. Note.Contoso").  
  
- Nezadávejte třída základní zprávy samostatně (například: "PM").  
  
- Není delší než 256 znaků pro každý název třídy zpráv.  
  
- Pokud se oblast formuláře nahradí celý formulář nebo výchozí stránku formuláře nezahrnují názvy standardní třídy zpráv. Můžete zadat názvy tříd standardní zprávu pouze u formulářů, přidejte novou stránku do formuláře nebo které jsou připojeny k dolní části formuláře. Další informace najdete v tématu [jak: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
  Visual Studio ověří formát názvů tříd zpráv při sestavování projektu.  
  
> [!NOTE]  
>  Visual Studio neověřuje, že jsou názvy tříd zpráv, které poskytnete správný nebo platný.  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Název formuláře a zpráva přehled tříd](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)   
 [Jak spolu fungují formulářů aplikace Outlook a položek](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)  
  
  