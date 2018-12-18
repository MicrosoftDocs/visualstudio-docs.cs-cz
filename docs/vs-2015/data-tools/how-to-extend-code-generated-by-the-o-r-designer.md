---
title: 'Postupy: rozšíření kódu vygenerovaného návrhářem relací | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14fd1f950d50f2cb71e56fc8b1e75ff60f3da0ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227911"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Postupy: rozšíření kódu vygenerovaného návrhářem relací objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Kód vygenerovaný [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] je znovu vygenerovány, když dojde ke změně tříd entit a dalších objektů na návrhové ploše. Z důvodu této opětovné generování kódu veškerý kód, který přidáte do vytvořeného kódu je obvykle při přepsat návrháře znovu vygeneruje kód. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Poskytuje možnost Generovat částečné třídy soubory, které můžete přidat kód, který nedojde k přepsání. Jedním z příkladů přidání vlastního kódu pro kód vygenerovaný [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] je přidání ověření dat na LINQ na třídy SQL (entita). Informace najdete v tématu [postupy: přidávání ověřování do tříd entit](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Přidání kódu do třídy Entity  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Vytvořit částečné třídy a přidat kód do třídy entity  
  
1.  Otevřete nebo vytvořte novou LINQ na třídy SQL soubor (**dbml** souborů) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Dvakrát klikněte **dbml** ve **Průzkumníka řešení**/**Průzkumník databáze**.)  
  
2.  V [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], klikněte pravým tlačítkem na třídu, pro který chcete přidat ověřování a pak klikněte na tlačítko **zobrazit kód**.  
  
     Otevře se Editor kódu s částečnou třídu pro třídy vybranou entitu.  
  
3.  Přidejte svůj kód v deklaraci částečné třídy pro třídu entity.  
  
## <a name="adding-code-to-a-datacontext"></a>Přidání kódu do položkou DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Vytvoření částečné třídy a přidat kód do položkou DataContext  
  
1.  Otevřete nebo vytvořte novou LINQ na třídy SQL soubor (**dbml** souborů) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Dvakrát klikněte **dbml** ve **Průzkumníka řešení**/**Průzkumník databáze**.)  
  
2.  V [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], klikněte pravým tlačítkem na prázdnou oblast v návrháři a potom klikněte na tlačítko **zobrazit kód**.  
  
     Otevře se Editor kódu s částečnou třídu pro DataContext.  
  
3.  Přidejte svůj kód v deklaraci částečné třídy pro DataContext.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Návod: Přidávání ověřování do tříd entit](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

