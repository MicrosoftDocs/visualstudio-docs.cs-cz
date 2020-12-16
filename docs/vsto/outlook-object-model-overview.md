---
title: Přehled modelu objektů aplikace Outlook
description: Zjistěte, jak můžete pracovat s objekty, které jsou k dispozici v objektovém modelu aplikace Outlook pro vývoj doplňků VSTO pro aplikaci Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83ada85ba346e83e5bc5ebc01e91b11be0e844e1
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528051"
---
# <a name="outlook-object-model-overview"></a>Přehled modelu objektů aplikace Outlook
  Pro vývoj doplňků VSTO pro systém Microsoft Office Outlook můžete pracovat s objekty, které jsou k dispozici v objektovém modelu aplikace Outlook. Objektový model aplikace Outlook poskytuje třídy a rozhraní, které představují položky v uživatelském rozhraní. Například <xref:Microsoft.Office.Interop.Outlook.Application> objekt představuje celou aplikaci, <xref:Microsoft.Office.Interop.Outlook.Folder> objekt představuje složku, která obsahuje e-mailové zprávy nebo jiné položky, a <xref:Microsoft.Office.Interop.Outlook.MailItem> objekt představuje e-mailovou zprávu.

 Toto téma poskytuje stručný přehled některých hlavních objektů v modelu objektu aplikace Outlook. Prostředky, ve kterých se můžete dozvědět víc o celém modelu objektů Outlook, najdete v [dokumentaci k objektovému modelu aplikace Outlook](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Přístup k objektům v projektu aplikace Outlook
 Outlook poskytuje mnoho objektů, se kterými můžete pracovat. Chcete-li model objektu používat efektivně, měli byste být obeznámeni s následujícími objekty nejvyšší úrovně:

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Objekt aplikace
 <xref:Microsoft.Office.Interop.Outlook.Application>Objekt představuje aplikaci Outlook a jedná se o objekt nejvyšší úrovně v modelu objektu aplikace Outlook. Mezi nejdůležitější členy tohoto objektu patří:

- Metoda [CreateItem –](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) , kterou můžete použít k vytvoření nové položky, jako je například e-mailová zpráva, úkol nebo schůzka.

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>Vlastnost, kterou můžete použít pro přístup k Windows, které zobrazuje obsah složky v uživatelském rozhraní Outlooku (UI).

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>Vlastnost, kterou můžete použít pro přístup k Windows, která zobrazují obsah jedné položky, například e-mailové zprávy nebo žádosti o schůzku.

  Chcete-li získat instanci <xref:Microsoft.Office.Interop.Outlook.Application> objektu, použijte pole aplikace `ThisAddIn` třídy ve vašem projektu. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Chcete-li zabránit upozorněním zabezpečení při použití vlastností a metod, které jsou blokovány ochranou modelu objektu aplikace Outlook, Získejte objekty aplikace Outlook z pole aplikace `ThisAddIn` třídy. Další informace najdete v tématu [specifické požadavky na zabezpečení pro řešení Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Objekt Explorer
 <xref:Microsoft.Office.Interop.Outlook.Explorer>Objekt představuje okno, které zobrazuje obsah složky, která obsahuje položky, jako jsou například e-mailové zprávy, úkoly nebo schůzky. <xref:Microsoft.Office.Interop.Outlook.Explorer>Objekt obsahuje metody a vlastnosti, které lze použít pro úpravu okna a události, které jsou vyvolány při změně okna.

 Chcete-li získat <xref:Microsoft.Office.Interop.Outlook.Explorer> objekt, proveďte jednu z následujících akcí:

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> <xref:Microsoft.Office.Interop.Outlook.Application> Pro přístup ke všem <xref:Microsoft.Office.Interop.Outlook.Explorer> objektům v aplikaci Outlook použijte vlastnost objektu.

- Použijte <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> metodu <xref:Microsoft.Office.Interop.Outlook.Application> objektu, chcete-li získat objekt <xref:Microsoft.Office.Interop.Outlook.Explorer> , který aktuálně má fokus.

- Použijte `GetExplorer` metodu <xref:Microsoft.Office.Interop.Outlook.Folder> objektu pro získání <xref:Microsoft.Office.Interop.Outlook.Explorer> pro aktuální složku.

### <a name="inspector-object"></a>Objekt Inspector
 <xref:Microsoft.Office.Interop.Outlook.Inspector>Objekt představuje okno, které zobrazuje jednu položku, například e-mailovou zprávu, úkol nebo schůzku. <xref:Microsoft.Office.Interop.Outlook.Inspector>Objekt obsahuje metody a vlastnosti, které lze použít pro úpravu okna a události, které jsou vyvolány při změně okna.

 Chcete-li získat <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, proveďte jednu z následujících akcí:

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> <xref:Microsoft.Office.Interop.Outlook.Application> Pro přístup ke všem <xref:Microsoft.Office.Interop.Outlook.Inspector> objektům v aplikaci Outlook použijte vlastnost objektu.

- Použijte <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> metodu <xref:Microsoft.Office.Interop.Outlook.Application> objektu, chcete-li získat objekt <xref:Microsoft.Office.Interop.Outlook.Inspector> , který aktuálně má fokus.

- Použijte `GetInspector` metodu konkrétní položky, například <xref:Microsoft.Office.Interop.Outlook.MailItem> nebo <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> , k načtení inspektoru, který je k němu přidružen.

### <a name="folder-object"></a>Objekt Folder
 <xref:Microsoft.Office.Interop.Outlook.Folder>Objekt představuje složku, která obsahuje e-mailové zprávy, kontakty, úkoly a další položky. Outlook poskytuje 16 výchozích <xref:Microsoft.Office.Interop.Outlook.Folder> objektů.

 Výchozí <xref:Microsoft.Office.Interop.Outlook.Folder> objekty jsou definovány <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> hodnotami výčtu. Třeba

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox odpovídá složce **Doručená pošta** v Outlooku.

 Příklad, který ukazuje, jak získat přístup k výchozímu <xref:Microsoft.Office.Interop.Outlook.Folder> a vytvořit nový <xref:Microsoft.Office.Interop.Outlook.Folder> , naleznete v tématu [How to: programing a Create a Custom Folder Items](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Objekt MailItem
 <xref:Microsoft.Office.Interop.Outlook.MailItem>Objekt představuje e-mailovou zprávu. <xref:Microsoft.Office.Interop.Outlook.MailItem> objekty jsou obvykle ve složkách, například **Doručená pošta**, **Odeslaná pošta** a **Faxy k odeslání**. <xref:Microsoft.Office.Interop.Outlook.MailItem> zpřístupňuje vlastnosti a metody, které lze použít k vytvoření a odeslání e-mailových zpráv.

 Příklad, který ukazuje, jak vytvořit e-mailovou zprávu, najdete v tématu [How to: program Create a email Item](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Objekt AppointmentItem
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>Objekt představuje schůzku, jednorázovou schůzku nebo opakovanou událost nebo schůzku ve složce **Kalendář** . <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>Objekt obsahuje metody, které provádějí akce, jako je například reakce na nebo předávání žádostí o schůzku a vlastnosti, které určují podrobnosti o schůzce, například umístění a čas.

 Příklad, který ukazuje, jak vytvořit schůzku, naleznete v tématu [How to: program Create a Meeting Request](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>Objekt TaskItem
 <xref:Microsoft.Office.Interop.Outlook.TaskItem>Objekt představuje úkol, který se má provést v zadaném časovém rámci. <xref:Microsoft.Office.Interop.Outlook.TaskItem> objekty se nacházejí ve složce **úkoly** .

 Chcete-li vytvořit úlohu, použijte metodu [CreateItem –](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) <xref:Microsoft.Office.Interop.Outlook.Application> objektu a předejte hodnotu <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> parametru.

### <a name="contactitem-object"></a>Objekt ContactItem
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Objekt představuje kontakt ve složce **kontaktů** . <xref:Microsoft.Office.Interop.Outlook.ContactItem> objekty obsahují různé kontaktní informace pro osoby, které představují, jako jsou například ulice, e-mailové adresy a telefonní čísla.

 Příklad, který ukazuje, jak vytvořit nový kontakt, naleznete v tématu [How to: program Add](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)a text to Contact Outlook. Příklad, který ukazuje, jak vyhledat existující kontakt, najdete v tématu [How to: program Search a search for the Contact (konkrétní kontakt](../vsto/how-to-programmatically-search-for-a-specific-contact.md)).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Použití dokumentace modelu objektu aplikace Outlook
 Úplné informace o objektovém modelu aplikace Outlook naleznete v odkazu na primární definiční sestavení (PIA) aplikace Outlook a referenční příručce k objektovému modelu VBA.

### <a name="primary-interop-assembly-reference"></a>Odkaz na primární definiční sestavení
 Odkaz na Outlook PIA documenters typy v primárních sestaveních spolupráce pro Outlook 2010. Další informace naleznete v tématu [odkaz na primární definiční sestavení aplikace Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Kromě poskytování informací pro všechny typy v PIA poskytuje tato dokumentace také další informace o struktuře PIA a příklady kódu pro běžné úlohy Outlook Automation.

### <a name="vba-object-model-reference"></a>Referenční dokumentace modelu objektu VBA
 Referenční model objektu VBA odkazuje na dokument model objektu aplikace Outlook, protože je vystavený pro jazyk Visual Basic for Application kód (VBA). Další informace najdete v tématu [referenční materiály k objektovému modelu aplikace Outlook 2010](/office/vba/api/overview/Outlook/object-model).

 Všechny objekty a členy v referenčním modelu objektu VBA odpovídají typům a členům v aplikacích Outlook PIA. Například objekt Inspector v odkazu modelu objektu VBA odpovídá <xref:Microsoft.Office.Interop.Outlook.Inspector> objektu v aplikaci Outlook PIA. I když Reference k objektovému modelu VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné překládat kód VBA v tomto odkazu na Visual Basic nebo Visual C#, pokud je chcete použít v projektu Add-In VSTO aplikace Outlook, který vytvoříte pomocí sady Visual Studio.

### <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s položkami kontaktů](../vsto/working-with-contact-items.md)|Obsahuje témata, která ukazují, jak provádět úlohy pomocí kontaktů.|
|[Práce s položkami pošty](../vsto/working-with-mail-items.md)|Obsahuje témata, která ukazují, jak provádět úlohy pomocí položek pošty.|
|[Práce se složkami](../vsto/working-with-folders.md)|Obsahuje témata, která ukazují, jak provádět úlohy se složkami.|
|[Práce s položkami kalendáře](../vsto/working-with-calendar-items.md)|Obsahuje témata, která ukazují, jak provádět úlohy s položkami kalendáře.|
|[Postupy: určení aktuální položky aplikace Outlook prostřednictvím kódu programu](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Ukazuje, jak zobrazit název aktuální složky a některé informace o vybrané položce.|
