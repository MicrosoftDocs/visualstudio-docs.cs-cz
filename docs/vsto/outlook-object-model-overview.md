---
title: Přehled modelu objektů aplikace Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6885968385725f4aa7d991309902ca712849c8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941188"
---
# <a name="outlook-object-model-overview"></a>Přehled modelu objektů aplikace Outlook
  Vývoj doplňků VSTO pro aplikaci Microsoft Office Outlook, můžete pracovat s objekty, které jsou k dispozici v modelu objektů aplikace Outlook. Model objektů aplikace Outlook obsahuje třídy a rozhraní, které představují položky v uživatelském rozhraní. Například <xref:Microsoft.Office.Interop.Outlook.Application> objekt představuje celé aplikace <xref:Microsoft.Office.Interop.Outlook.Folder> objekt představuje složku, která obsahuje e-mailové zprávy nebo jiné položky a <xref:Microsoft.Office.Interop.Outlook.MailItem> objekt představuje e-mailové zprávy.  
  
 Toto téma nabízí stručný přehled o některé hlavní objekty v objektovém modelu aplikace Outlook. Prostředky, kde můžete dozvědět více o celý model objektů aplikace Outlook, naleznete v tématu [použijte dokumentaci modelu objektů aplikace Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak Outlook použití I: vytvoření sestavy vlastní úloha?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Přístup k objektům v projektu aplikace Outlook  
 Aplikace Outlook obsahuje mnoho objektů, se kterými můžete pracovat. Objektový model efektivně používat, byste měli znát následující objekty nejvyšší úrovně:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Folder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Objekt aplikace  
 <xref:Microsoft.Office.Interop.Outlook.Application> Objekt představuje aplikaci Outlook a je to objekt nejvyšší úrovně v modelu objektů aplikace Outlook. Některé z vašich nejdůležitějších členům tohoto objektu patří:  
  
- [Createitem –](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) metodu, která slouží k vytvoření nové položky, například e-mailové zprávy, úkolu nebo události.  
  
- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> Vlastnost, která vám umožní přístup k systému windows, které zobrazují obsah složky v uživatelském rozhraní (UI) aplikace Outlook.  
  
- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> Vlastnost, která vám umožní přístup k systému windows, které zobrazují obsah jedné položky, jako je například požadavek e-mailové zprávy nebo schůzky.  
  
  Chcete-li získat instanci <xref:Microsoft.Office.Interop.Outlook.Application> objektu, použití pole aplikace `ThisAddIn` třídu ve vašem projektu. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Pokud chcete vyhnout upozornění zabezpečení při použití vlastnosti a metody, které jsou blokovány ochrana modelů objektů aplikace Outlook, získání objektů aplikace Outlook z pole aplikace `ThisAddIn` třídy. Další informace najdete v tématu [specifické aspekty zabezpečení pro řešení Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Průzkumník objektů  
 <xref:Microsoft.Office.Interop.Outlook.Explorer> Objekt představuje okno, které se zobrazí obsah složky obsahující položky, jako jsou e-mailové zprávy, úlohy nebo události. <xref:Microsoft.Office.Interop.Outlook.Explorer> Objekt obsahuje metody a vlastnosti, které vám umožní upravit v okně a události, které jsou vyvolány při změně okna.  
  
 Chcete-li získat <xref:Microsoft.Office.Interop.Outlook.Explorer> objektu, proveďte jednu z následujících akcí:  
  
-   Použití <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> vlastnost <xref:Microsoft.Office.Interop.Outlook.Application> objektu pro přístup k veškerému <xref:Microsoft.Office.Interop.Outlook.Explorer> objekty v aplikaci Outlook.  
  
-   Použití <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> metodu <xref:Microsoft.Office.Interop.Outlook.Application> můžete získat <xref:Microsoft.Office.Interop.Outlook.Explorer> , že má právě fokus.  
  
-   Použití `GetExplorer` metodu <xref:Microsoft.Office.Interop.Outlook.Folder> můžete získat <xref:Microsoft.Office.Interop.Outlook.Explorer> pro aktuální složku.  
  
### <a name="inspector-object"></a>Kontrola objektu  
 <xref:Microsoft.Office.Interop.Outlook.Inspector> Objekt představuje okno, které zobrazí konkrétní položce například e-mailové zprávy, úkolu nebo události. <xref:Microsoft.Office.Interop.Outlook.Inspector> Objekt obsahuje metody a vlastnosti, které vám umožní upravit v okně a události, které jsou vyvolány při změně okna.  
  
 Chcete-li získat <xref:Microsoft.Office.Interop.Outlook.Inspector> objektu, proveďte jednu z následujících akcí:  
  
-   Použití <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> vlastnost <xref:Microsoft.Office.Interop.Outlook.Application> objektu pro přístup k veškerému <xref:Microsoft.Office.Interop.Outlook.Inspector> objekty v aplikaci Outlook.  
  
-   Použití <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> metodu <xref:Microsoft.Office.Interop.Outlook.Application> můžete získat <xref:Microsoft.Office.Interop.Outlook.Inspector> , že má právě fokus.  
  
-   Použití `GetInspector` metoda konkrétní položky, jako například <xref:Microsoft.Office.Interop.Outlook.MailItem> nebo <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, k načtení Inspector, který je spojen s ním.  
  
### <a name="folder-object"></a>Objekt složky  
 <xref:Microsoft.Office.Interop.Outlook.Folder> Objekt představuje složku, která obsahuje e-mailové zprávy, kontakty, úkoly a další položky. Aplikace Outlook poskytuje 16 výchozí <xref:Microsoft.Office.Interop.Outlook.Folder> objekty.  
  
 Výchozí hodnota <xref:Microsoft.Office.Interop.Outlook.Folder> objekty jsou definovány <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> hodnot výčtu. Například  
  
 Odpovídá Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox **doručené pošty** složky aplikace Outlook.  
  
 Příklad, který ukazuje, jak získat přístup k výchozí <xref:Microsoft.Office.Interop.Outlook.Folder> a vytvořte nový <xref:Microsoft.Office.Interop.Outlook.Folder>, naleznete v tématu [postupy: vytváření vlastních položek složek prostřednictvím kódu programu](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Objekt MailItem  
 <xref:Microsoft.Office.Interop.Outlook.MailItem> Objekt představuje e-mailové zprávy. <xref:Microsoft.Office.Interop.Outlook.MailItem> objekty jsou obvykle ve složkách, jako je například **doručené pošty**, **odeslaná**, a **pošta k odeslání**. <xref:Microsoft.Office.Interop.Outlook.MailItem> poskytuje vlastnosti a metody, které slouží k vytvoření a odeslání e-mailové zprávy.  
  
 Příklad, který ukazuje, jak vytvořit e-mailu, najdete v části [postupy: programové vytváření položek e-mailu](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Objekt částí AppointmentItem  
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Objekt představuje schůzku, jednorázovou událost nebo opakovaná událost nebo schůzku v **kalendáře** složky. <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Objekt obsahuje metody, které provádějí akce, jako je zpracování nebo předávání žádostí o schůzku a vlastnosti, které určují podrobnosti schůzky, jako je například umístění a čas.  
  
 Příklad, který ukazuje, jak vytvořit schůzku s cílem, naleznete v tématu [postupy: vytváření žádostí o schůzku prostřednictvím kódu programu](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Objekt TaskItem  
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> Objekt představuje úlohy provádět v rámci zadaného časového rámce. <xref:Microsoft.Office.Interop.Outlook.TaskItem> objekty jsou umístěny v **úlohy** složky.  
  
 Chcete-li vytvořit úlohu, použijte [createitem –](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) metodu <xref:Microsoft.Office.Interop.Outlook.Application> objektu a předejte hodnotu <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> parametru.  
  
### <a name="contactitem-object"></a>Objekt ContactItem  
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Objekt představuje kontakt v **kontakty** složky. <xref:Microsoft.Office.Interop.Outlook.ContactItem> objekty obsahují celou řadu kontaktní informace pro osoby, které představují, jako je například adresu, e-mailových adres a telefonních čísel.  
  
 Příklad, který ukazuje, jak vytvořit nový kontakt, naleznete v tématu [postupy: přidávání položky ke kontaktům aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Příklad, který ukazuje, jak vyhledat existující kontakt, naleznete v tématu [postupy: hledání konkrétního kontaktu prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Použijte dokumentaci modelu objektů aplikace Outlook  
 Podrobnější informace o modelu objektů aplikace Outlook mohou odkazovat na primární sestavení vzájemné spolupráce (PIA) odkaz na aplikaci Outlook a referenční dokumentace objektového modelu VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Odkaz na primární spolupracující sestavení  
 Odkaz na aplikaci Outlook PIA dokumentů typy v sestavení primární spolupráce pro Outlook 2010. Další informace najdete v tématu [odkaz na primární spolupracující sestavení aplikace Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Kromě toho, že informace pro všechny typy v sestavení PIA, tato dokumentace obsahuje také další informace o struktuře PIA a příklady kódu pro běžné úlohy automatizace aplikace Outlook.  
  
### <a name="vba-object-model-reference"></a>Referenční dokumentace objektového modelu VBA  
 Referenční dokumentace objektového modelu VBA dokumenty objektový model aplikace Outlook jako jeho zveřejnění do jazyka Visual Basic pro kód Applications (VBA). Další informace najdete v tématu [referenční dokumentace objektového modelu aplikace Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Všechny objekty a členy v referenční dokumentace objektového modelu VBA odpovídají typy a členy v Outlooku PIA. Například objekt inspektoru v referenční dokumentace objektového modelu VBA odpovídá <xref:Microsoft.Office.Interop.Outlook.Inspector> objektu v aplikaci Outlook PIA. I když referenční dokumentace objektového modelu VBA poskytuje příklady kódu pro většinu vlastnosti, metody a události, pokud chcete použít v projektu doplňku VSTO Outlooku, který vytvoříte pomocí musí překládat kód VBA v této referenční dokumentace jazyka Visual Basic nebo Visual C# Visual Studio.  
  
### <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Práce s položkami kontaktů](../vsto/working-with-contact-items.md)|Obsahuje témata, které ukazují, jak k provádění úloh s kontakty.|  
|[Práce s položkami pošty](../vsto/working-with-mail-items.md)|Obsahuje témata, které ukazují, jak k provádění úloh s položkami pošty.|  
|[Práce se složkami](../vsto/working-with-folders.md)|Obsahuje témata, které ukazují, jak k provádění úloh se složkami.|  
|[Práce s položkami kalendáře](../vsto/working-with-calendar-items.md)|Obsahuje témata, které ukazují, jak k provádění úloh s položkami kalendáře.|  
|[Postupy: určení aktuální položky aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Ukazuje, jak zobrazit název aktuální složky a některé informace o vybrané položce.|  
  