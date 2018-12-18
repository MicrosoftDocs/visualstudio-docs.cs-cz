---
title: 'Postupy: použití editoru výrazů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0c41de63b4163f1fd259ffa4adcef63cad92e351
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181712"
---
# <a name="how-to-use-the-expression-editor"></a>Postupy: použití editoru výrazů
Je Editor výrazů [!INCLUDE[wfd1](../includes/wfd1-md.md)] ovládací prvek, který se používá v mnoha aktivit pracovního postupu jako způsob zadávání a vyhodnocování těchto výrazů. Editor výrazů nabízí plnohodnotný IDE editační rozhraní, včetně IntelliSense, zabarvení, ParamInfo podtržení vlnovkou u chyb, kromě jiných funkcí. Kompilátor ověří výraz poté, co je zadána. Pokud výraz není platný, zobrazí se ikona chyby. V editoru můžete otevřít také jako **Editor výrazů** dialogové okno.  
  
 Výrazy jsou hodnoty literálu nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kód vázán na argumenty nebo vlastnosti. Obsahující hodnoty prvků (např. proměnné, konstanty, literály, vlastnosti), které jsou spojené s operacemi na novou hodnotu. Výrazy jsou zapsány pomocí syntaxe VB.NET i v případě, že aplikace je v aplikaci pomocí jazyka C#. To znamená, že velikost písmen nezáleží, porovnání je provedeno pomocí jediného rovnítko (=") namísto ("=="), logické operátory jsou slova"a"a"nebo"namísto symboly" & & "a"&#124;&#124;", a **nic**  se použije namísto **null**. Další informace o výrazy a operátory ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a některé ukázky najdete v tématu [operátory a výrazy v jazyce Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).  
  
 **Editor výrazů** chová takto:  
  
-   Pokud fokus není v editoru výrazů, vypadá jako na běžný ovládací prvek TextBlock.  
  
-   V editoru výrazů po výběru vypadat a jak se bude chovat jako ovládací prvek editoru výrazů. Po ztratí fokus, it znovu vypadá jako regulární TextBlock.  
  
-   Pokud vám soustředit se na Editor výrazů v Návrháři postupu provádění se změněným hostováním, pak se chová stejně jako textové pole. Jakmile v Návrháři postupu provádění se změněným hostováním se ztratí fokus, editoru výrazů bude vypadat jako regulární TextBlock znovu.  
  
> [!NOTE]
>  Technologie IntelliSense pro Editor výrazů je k dispozici jen uvnitř sady [!INCLUDE[vs2010](../includes/vs2010-md.md)]. V obou [!INCLUDE[vs2010](../includes/vs2010-md.md)] a provádění se změněným hostováním scénáře, kompilátor ověří výraz poté, co se zadají a editor výrazů zobrazuje ikonu chyby, pokud výraz není platný.  
  
### <a name="using-the-expression-editor"></a>Pomocí editoru výrazů  
  
1.  V [!INCLUDE[vs2010](../includes/vs2010-md.md)], otevřete projekt nového nebo existujícího pracovního postupu.  
  
2.  Přidání, například <xref:System.Activities.Statements.Assign> aktivitu do pracovního postupu.  
  
    > [!NOTE]
    >  Více aktivit pracovního postupu mít editory výrazu. Výraz objekty TextBlock se také zobrazují v Návrhář proměnných, Návrhář argumentů a Návrhář dynamických argumentů. <xref:System.Activities.Statements.Assign> Aktivita slouží jako příklad.  
  
3.  Klikněte na levý výraz editoru v Návrháři aktivit pro <xref:System.Activities.Statements.Assign> aktivity.  
  
     Šedé vodoznak řetězce  **\<k >** a  **\<zadejte výraz jazyka VB. >** jsou výchozí text řetězce pro výraz editory v <xref:System.Activities.Statements.Assign> aktivity.  
  
4.  Při zadávání výrazu. Pokud zadáte řetězec, ujistěte se, že chcete vložit řetězec v uvozovkách. Pokud budete chtít vázat argument výrazu na proměnnou, ponechte uvozovky.  
  
     Jakmile budete hotovi, vyberte oblast nebo oblasti mimo Editor výrazů přesune fokus na jiné části návrháře. To způsobí, že kompilátor, aby ověření výrazu, jak je popsáno výše.  
  
     Alternativní způsob, jak zadat nebo upravit výraz je kliknout na tři tečky vedle názvu vlastnosti v mřížce vlastností. Tím se otevře **Editor výrazů** jako dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>