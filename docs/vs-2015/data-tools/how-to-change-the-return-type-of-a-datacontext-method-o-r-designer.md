---
title: 'Postupy: Změna návratového typu metody DataContext (O R Designer) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4999c9fd273b78ff740e53c25bbe5a4b0a3017f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211741"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Postupy: Změna návratového typu metody DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Návratový typ <xref:System.Data.Linq.DataContext> – metoda (založeno na uložená procedura nebo funkce) se liší v závislosti na tom, kde vyřaďte uloženou proceduru nebo funkci v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Pokud přetáhnete položku přímo do existující entity třídy, <xref:System.Data.Linq.DataContext> metodu, která má návratový typ třídy entita se vytvoří (Pokud je schéma dat vrácené uloženou proceduru nebo funkci odpovídá obrazec třídy entity). Pokud přetáhnete položku na prázdnou oblast [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], <xref:System.Data.Linq.DataContext> vytvořené metodou, která vrací automaticky generovanému typu. Můžete změnit návratový typ <xref:System.Data.Linq.DataContext> metoda po přidání do podokna metody. Zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metoda, vyberte ho a klikněte **návratový typ** vlastnost v **vlastnosti** okna.  
  
> [!NOTE]
>  Nejde vrátit zpět <xref:System.Data.Linq.DataContext> metody, které mají návratový typ nastavena na třídu entity k vrácení automaticky generovaný typ pomocí **vlastnosti** okna. Vrátit zpět <xref:System.Data.Linq.DataContext> metodu pro návrat na automaticky generovaný typ, je třeba přetáhnout na původní objekt databáze znovu do Návrháře relací objektů.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Změna návratového typu metody DataContext z automaticky generovaný typ pro třídu entity  
  
1.  Vyberte <xref:System.Data.Linq.DataContext> metoda v podokně metody.  
  
2.  Vyberte **návratový typ** v **vlastnosti** okna a pak vyberte dostupné entity třídy v **návratový typ** seznamu. Pokud třída požadované entity není v seznamu, přidejte ji tak nebo jej vytvořit v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ho přidat do seznamu.  
  
3.  Uložte soubor .dbml.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Chcete-li změnit zpět na automaticky generovaný typ návratového typu metody DataContext z třídy entity  
  
1.  Vyberte <xref:System.Data.Linq.DataContext> metoda v podokně metody a odstraňte ho.  
  
2.  Přetáhněte objekt databáze z **Průzkumníka serveru**/**Průzkumník databáze** na prázdnou oblast Návrháře relací objektů.  
  
3.  Uložte soubor .dbml.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

