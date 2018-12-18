---
title: Vytváření datových aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291307"
---
# <a name="creating-data-applications"></a>Vytváření datových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio poskytuje mnoho nástrojů doby návrhu můžete vytvářet aplikace pro přístup k datům. Tento úvod nabízí přehled základních procesů zapojených do vytváření aplikací, které pracují s daty. Zde uvedené informace záměrně přeskočí mnoho podrobností a slouží jako zdroj informací a všeobecných bod, který má mnoho jiných stránek s nápovědou spojených s vytvořením datové aplikace.  
  
 Při vývoji aplikací přistupujících k datům v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], budete mít jiné požadavky. V některých případech můžete jednoduše chtít zobrazit data ve formuláři. V jiných případech může být třeba navrhnout způsob, jak sdílet informace s jinými aplikacemi nebo procesy.  
  
 Bez ohledu na to, co děláte s daty existují určité základní principy, které byste měli rozumět. Nikdy můžete potřebovat znát některé podrobnosti zpracování dat – například můžete nikdy potřebovat programově vytvořit databázi, ale je velmi užitečné rozumět základním pojmům dat, stejně jako nástroje data (průvodci a návrháři) k dispozici v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Typické datová aplikace používá většina procesů znázorněných na následujícím diagramu:  
  
 ![Datový symbol cyklu](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
Datový cyklus  
  
 Když vytváříte aplikaci, si můžete Představte úkol, který se snažíte dosáhnout. Pomocí následujících částí využijte pomoc při hledání [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje a objekty, které jsou k dispozici.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje průvodce ke zjednodušení několika procesů je vidět na předchozím obrázku. Například systém **Průvodce konfigurací zdroje dat** poskytuje aplikaci dostatek informací k připojení k datům, vytvoření typové datové sady pro příjem dat a přenést data do aplikace.  
  
 Pokud chcete rychle zobrazit jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vám pomůže při vývoji datových aplikací, najdete v článku [návod: vytvoření jednoduché datové aplikace](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Připojení k datům  
 Přenést data do aplikace (a odeslat změny zpět do zdroje dat), je potřeba navázat nějaký druh obousměrné komunikace. Tato obousměrná komunikace je obvykle zpracovávána objekty v datovém modelu.  
  
 Například `TableAdapter` připojí aplikace, které používají datové sady do databáze, a <xref:System.Data.Objects.ObjectContext> entity v Entity Framework připojí k databázi. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje několik nástrojů, které pomáhají při vytváření připojení, které můžete použít v aplikaci. Další informace o připojení aplikace k datům najdete v tématu [připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Další informace o použití datových sad pro připojení aplikace k datům v databázi, naleznete v tématu [návod: připojování k datům v databázi (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Příprava aplikace na příjem dat  
 Pokud vaše aplikace používá odpojený datový model je třeba dočasně ukládat data v aplikaci při práci s ní. Visual Studio poskytuje nástroje, které pomáhají vytvořit objekty, které vaše aplikace používá dočasné úložiště dat: datové entity a [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objekty.  
  
> [!NOTE]
>  Aplikace, která používá odpojený datový model se obvykle připojení k databázi, spustí dotaz přinášející data do aplikace, odpojí se od databáze a pak pracuje s daty v režimu offline před opětovným připojením a aktualizací databáze.  
  
 Další informace o vytvoření typové datové sady v aplikaci najdete v tématu [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). Další informace o použití datových sad v n vrstvé aplikace najdete v tématu [oddělování datových sad a TableAdapters do různých projektů](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Informace o vytvoření datové sady, dokončete postupy uvedené v [návod: vytvoření datové sady pomocí návrháře datových sad](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Další informace o vytvoření [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objekty, dokončete postupy uvedené v [návod: vytvoření třídy LINQ to SQL (O R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Načítání dat do aplikace  
 Jestli vaše aplikace používá odpojený datový model nebo Ne, musíte být schopni načíst data do vaší aplikace. Data do aplikace přenést spuštěním dotazů nebo uložených procedur proti databázi. Aplikace, které ukládají data v datových sadách, spouštějí dotazy a uložené procedury pomocí `TableAdapter`s, že aplikace, které ukládají data v entitách, spouštějí dotazy pomocí [technologii LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) nebo přímým připojením entit přímo na uložené procedury. Další informace o vytváření a úpravy dotazů, které používají TableAdapters, naleznete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md) a [jak: Edit TableAdapter Queries](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Další informace o načtení dat do datové sady a spouštění dotazů a uložených procedur, naleznete v tématu [načítání dat do aplikace](../data-tools/fetching-data-into-your-application.md).  
  
 Další informace o načtení dat do datové sady, dokončete postupy uvedené v [návod: zobrazení dat ve formuláři Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) a prozkoumat kód v obslužné rutině události nahrání formuláře.  
  
 Další informace o načtení dat do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objekty, dokončete postupy uvedené v [návod: vytvoření třídy LINQ to SQL (O R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Zjistěte, jak vytvořit a spustit dotaz SQL, najdete v článku [postupy: vytvoření a provedení příkazu SQL, že vrátí řádky](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Zjistěte, jak spustit uloženou proceduru, najdete v článku [postupy: spuštění uložené procedury této vrací řádky](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Zobrazení dat ve formulářích  
 Po načtení dat do vaší aplikace, které obvykle můžete zobrazit ve formuláři, uživatelé mohli zobrazit nebo upravit. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), kde můžete přetáhnout položky do formulářů k automatickému vytvoření ovládacích prvků vázaných na data, které zobrazují data. Další informace o datových vazbách a zobrazení dat uživatelům, naleznete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Další informace o představení dat uživatelům, dokončete postupy uvedené v následujících návodech (věnujte zvláštní pozornost procesu přetažení položek z **zdroje dat** okno):  
  
-   [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Vytvoření vazby ovládacích prvků WPF k datové službě WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Návod: Vazba ovládacích prvků Silverlight ke službě WCF Data](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Úpravy dat v aplikaci  
 Jakmile uživatelům byla předložena data, se budou pravděpodobně chtít upravit přidáním nových záznamů a úpravou a odstraňováním záznamů před odesláním dat zpět do databáze.  
  
 Další informace o práci s daty, jakmile budou načtena do datové sady, naleznete v tématu [úpravy dat v aplikace](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Ověřování dat  
 Při provádění změn dat, obvykle můžete ověřit změny před povolením hodnoty, které mají být přijaty zpět do datové sady nebo zapsány do databáze. *Ověření* je název procesu pro ověření, že jsou tyto nové hodnoty přijatelné pro požadavky vaší aplikace. Můžete přidat logiku, která zkontroluje hodnoty aplikace při změně. Visual Studio poskytuje nástroje, které pomáhají při přidávání kódu, který ověřuje data při změnách řádků a sloupců. Další informace najdete v tématu [ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Zjistěte, jak přidat data ověření do vaší aplikace, najdete v článku [návod: Přidání ověření do datové sady](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 Informace o přidání ověřování do datové sady, která je rozdělena na n vrstvou aplikaci najdete v tématu [přidání ověřování do vícevrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Ukládání dat  
 Po provedení změn v aplikaci (a jejich ověření), obvykle chcete odeslat změny zpět do databáze. Aplikace, které obvykle ukládají data v datových sadách pomocí vlastnosti TableAdapterManager uložit data. Další informace najdete v tématu [TableAdapterManager – přehled](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Aplikace Entity Framework používají <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda uložit data.  
  
 Další informace o odesílání aktualizovaných dat do databáze najdete v tématu [ukládání dat](../data-tools/saving-data.md).  
  
 Chcete-li zjistěte, jak odeslat aktualizovaná data z datové sady do databáze, dokončete postupy uvedené v [návod: ukládání dat z tabulek souvisejících dat (hierarchická aktualizace)](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>Související témata  
 [Přehled datových aplikacích v sadě Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Poskytuje odkazy na témata týkající se vytváření aplikací, které pracují s daty.  
  
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Obsahuje odkazy na témata o tom, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k připojení aplikace k datům a vytvoření zdrojů dat pro vaše aplikace.  
  
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Obsahuje odkazy na témata, která popisují, jak pracovat s modely dat ve vaší aplikaci, včetně datových sad a modelů Entity Data Model.  
  
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)  
 Obsahuje odkazy na témata popisující, jak načíst data do vaší aplikace.  
  
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Obsahuje odkazy na témata, která popisují, jak k vazbě Windows Forms ovládací prvky, ovládacích prvků WPF a ovládací prvky Silverlight do zdrojů.  
  
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)  
 Obsahuje odkazy na témata popisující změnu dat v aplikaci.  
  
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Obsahuje odkazy na témata popisující přidání ověření datových změn.  
  
 [Ukládání dat](../data-tools/saving-data.md)  
 Obsahuje odkazy na témata, která popisují, jak odeslat aktualizovaná data z vaší aplikace k databázi nebo jak uložit do jiných formátů, například XML.  
  
 [Nástroje pro práci se zdroji dat v sadě Visual Studio](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Obsahuje odkazy na témata týkající se nástrojů, které můžete použít pro práci se zdroji dat v sadě Visual Studio, jako **zdroje dat** okno a ADO.NET Entity Data Model Designer.