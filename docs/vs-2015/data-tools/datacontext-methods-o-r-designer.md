---
title: Metody DataContext (O R Designer) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ccf32d4af0bd16032c4601b054be6407071753f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200457"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) metody (v kontextu [LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) jsou metody <xref:System.Data.Linq.DataContext> třída, která spustí uložené postupy a funkce v databázi.  
  
 <xref:System.Data.Linq.DataContext> Třída je [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídu, která funguje jako přenos mezi databází systému SQL Server a [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] tříd entit namapována na tuto databázi. <xref:System.Data.Linq.DataContext> Třída obsahuje metody pro připojení k databázi a manipulace s daty v databázi a informace o připojovacím řetězci. Ve výchozím nastavení <xref:System.Data.Linq.DataContext> třída obsahuje několik metod, které bude možné volat, například <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu, která odešle aktualizovaná data z [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy do databáze. Můžete také vytvořit další <xref:System.Data.Linq.DataContext> metody, které se mapují na uložené procedury a funkce. Jinými slovy, volání těchto metod vlastní Spustí uloženou proceduru nebo funkci v databázi, která <xref:System.Data.Linq.DataContext> metoda je namapována na. Můžete přidat nové metody <xref:System.Data.Linq.DataContext> třídy stejně, jako byste přidali metody rozšíření libovolné třídy. Nicméně v diskuzích k žádostem o <xref:System.Data.Linq.DataContext> metody v kontextu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], je <xref:System.Data.Linq.DataContext> metody, které se mapují na uložené procedury a funkce, které byly diskutovány.  
  
## <a name="methods-pane"></a>Podokno metody  
 <xref:System.Data.Linq.DataContext> metody, které se mapují na uložené procedury a funkce jsou zobrazeny v podokně metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Podokno metody je v podokně po straně **entity** podokně (hlavní návrhová plocha). Podokno metody jsou uvedeny všechny <xref:System.Data.Linq.DataContext> metody, které jste vytvořili pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Ve výchozím nastavení podokno metody je prázdná. Přetáhněte uložené procedury nebo funkce z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] vytvořit <xref:System.Data.Linq.DataContext> metody a naplňte jimi podokno metody. Další informace najdete v tématu [jak: metod vytvoření DataContext namapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Otevření a zavření podokno metody kliknutím pravým tlačítkem myši [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a pak levým na **skrýt podokno metody** nebo **zobrazit podokno metody**, nebo použijte klávesovou zkratku CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Dva typy metod DataContext  
 Metody DataContext jsou tyto metody, které se mapují na uložené procedury a funkce v databázi. Můžete vytvořit a přidat jednu metodu DataContext v podokně metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Existují dva odlišné typy <xref:System.Data.Linq.DataContext> metody; ty, které vrátí jeden nebo více sad výsledků dotazu a ty, které nejsou:  
  
-   <xref:System.Data.Linq.DataContext> metody, které vrací jeden nebo více sad výsledků dotazu:  
  
     Vytvořit tento druh <xref:System.Data.Linq.DataContext> metodu, když vaše aplikace potřebuje pouze pro spouštění uložených procedur a funkcí v databázi a výsledky jsou vráceny. Další informace najdete v tématu [jak: metod vytvoření DataContext namapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, a <xref:System.Data.Linq.IMultipleResults>.  
  
-   <xref:System.Data.Linq.DataContext> metody, které nevracejí sad výsledků dotazu: například vloží aktualizace a odstraní pro konkrétní entitu třídu.  
  
     Vytvořit tento druh <xref:System.Data.Linq.DataContext> metodu, pokud má vaše aplikace pro spuštění uložené procedury místo použití výchozí [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování při ukládání změněných dat mezi třídu entity a databází. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Návratové typy metod DataContext  
 Při přetažení uložených procedur a funkcí z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], návratový typ vytvořeného <xref:System.Data.Linq.DataContext> metoda se liší v závislosti na tom, kde je vyřadit položku. Přetažení položek přímo do existující entity třídy vytvoří <xref:System.Data.Linq.DataContext> metoda s návratovým typem třídy entity; přetažení položek na prázdnou oblast [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (v obou podokno) vytvoří <xref:System.Data.Linq.DataContext> metodu, která vrací automaticky generovanému typu. Automaticky generovanému typu, který je vytvořen má název, který odpovídá uloženou proceduru nebo název funkce a vlastnosti, které se mapují na pole vrácené uloženou proceduru nebo funkci.  
  
> [!NOTE]
>  Můžete změnit návratový typ <xref:System.Data.Linq.DataContext> metoda po přidání do podokna metody. Zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metoda, vyberte ho a zkontrolujte **návratový typ** vlastnost **vlastnosti** okna. Další informace najdete v tématu [postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Objekty, které můžete přetáhnout z databáze na plochu návrháře relací objektů bude mít název automaticky na základě názvu objekty v databázi. Pokud přetáhnete na stejný objekt více než jednou, číslo je připojen na konec nový název, který odlišuje názvy. Pokud názvy databázových objektů obsahují mezery nebo znaky nepodporované v jazyce Visual Basic nebo C#, se nahradí mezery nebo neplatné znaky podtržítkem.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Uložené procedury](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

