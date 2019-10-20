---
title: 'Postupy: definice a používání delegátů aktivit v Návrhář postupu provádění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603856"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Postupy: definice a využívání delegátů aktivit v Návrhář postupu provádění
[!INCLUDE[net_v45](../includes/net-v45-md.md)] obsahuje nového předem připraveného návrháře pro aktivitu <xref:System.Activities.Statements.InvokeDelegate>. Tento návrhář lze použít k přiřazení delegátů aktivitě, která je odvozena od <xref:System.Activities.ActivityDelegate>, například <xref:System.Activities.ActivityAction> nebo <xref:System.Activities.ActivityFunc%601>.

### <a name="define-an-activity-delegate"></a>Definovat delegáta aktivity

1. V [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] vyberte **soubor**, **Nový**, **projekt**. Na levé straně vyberte uzel **pracovního postupu** a na pravé straně šablonu **konzolové aplikace pracovního postupu** . Pojmenujte projekt (Pokud je to potřeba) a klikněte na **OK**.

2. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **Přidat**, **Nová položka.** . Na levé straně vyberte uzel **pracovního postupu** a na pravé straně šablonu **aktivity** . Pojmenujte novou aktivitu **MyForEach. XAML** a klikněte na tlačítko **OK**. Aktivita se otevře v Návrháři pracovních postupů.

3. V Návrháři pracovních postupů klikněte na kartu **argumenty** .

4. Klikněte na **vytvořit argument**. Pojmenujte nové **položky**argumentu.

5. Ve sloupci **typ argumentu** vyberte **pole z [T]** .

6. V prohlížeči typů vyberte **objekt**. Klikněte na tlačítko **OK**.

7. Znovu klikněte na tlačítko **vytvořit argument** . Pojmenujte nový **hlavní část**argumentu. Ve sloupci **směr** pro nový argument vyberte **vlastnost**.

8. Ve sloupci Typ argumentu vyberte **Vyhledat typy...**

9. V prohlížeči typu zadejte **ActivityAction** do pole **název typu** . Ve stromovém zobrazení vyberte **ActivityAction \<T >** . V rozevíracím seznamu vyberte **objekt** , který se zobrazí, **\<Object >** k argumentu přiřadit typ ActivityAction.

10. Přetáhněte aktivitu <xref:System.Activities.Statements.While> z části **Flow řízení** v sadě nástrojů na plochu návrháře.

11. Vyberte aktivitu <xref:System.Activities.Statements.While> a vyberte kartu **proměnné** .

12. Vyberte **vytvořit proměnnou**. Pojmenujte nový **index**proměnné.

13. Ve sloupci **typ proměnné** vyberte **Int32**. Tento **obor** ponechte jako **while**a **výchozí** sloupec je prázdný.

14. Nastavte vlastnost **Condition** aktivity <xref:System.Activities.Statements.While> tak, aby **< položky indexována. délka;** .

15. Přetáhněte aktivitu <xref:System.Activities.Statements.InvokeDelegate> z oddílu **primitivs** v sadě nástrojů na **tělo** aktivity <xref:System.Activities.Statements.While>.

16. V rozevíracím seznamu delegáta vyberte **text** .

17. V mřížce **vlastnosti** aktivity <xref:System.Activities.Statements.InvokeDelegate> klikněte na **...** na tlačítko ve vlastnosti **argumenty delegáta** .

18. Do sloupce **hodnota** argumentu pojmenovaného **argumentu**zadejte **Items [index]** . Kliknutím na tlačítko **OK** zavřete dialogové okno **DelegateArguments** .

19. Přetáhněte aktivitu <xref:System.Activities.Statements.Assign> na vodorovnou čáru pod aktivitou <xref:System.Activities.Statements.InvokeDelegate>. Vytvoří se aktivita <xref:System.Activities.Statements.Assign> a automaticky se vytvoří aktivita <xref:System.Activities.Statements.Sequence>, která bude obsahovat dvě aktivity v části **tělo** aktivity **MyForEach** . Sekvence je nutná, protože oddíl **body** může obsahovat pouze jednu aktivitu. Automatické vytvoření nové aktivity <xref:System.Activities.Statements.Sequence> je nová funkce [!INCLUDE[net_v45](../includes/net-v45-md.md)].

20. Nastavte vlastnost **Property aktivity <xref:System.Activities.Statements.Assign> na** **index**. Nastavte vlastnost **Value** aktivity **přiřadit** na **index + 1**.

    Vlastní aktivita **MyForEach** nyní vyvolá libovolnou aktivitu jednou pro každou předanou hodnotu prostřednictvím kolekce **Items** s hodnotami v kolekci jako vstupy pro aktivitu.

### <a name="use-the-custom-activity-in-a-workflow"></a>Použití vlastní aktivity v pracovním postupu

1. Sestavte projekt stisknutím **kombinace kláves CTRL + SHIFT + B**.

2. V **Průzkumník řešení**otevřete **Workflow1. XAML** v návrháři.

3. Přetáhněte aktivitu **MyForEach** ze sady nástrojů na plochu návrháře. Aktivita bude v části sady nástrojů se stejným názvem jako projekt.

4. Nastavte vlastnost **Items** aktivity **MyForEach** na **New Object [] {1, "ABC"}** .

5. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> z oddílu **primitivs** v sadě nástrojů do oddílu **Delegate: body** aktivity **MyForEach** .

6. Nastavte vlastnost **text** aktivity <xref:System.Activities.Statements.WriteLine> na **argument. ToString ()** .

   Při spuštění pracovního postupu zobrazí Konzola následující:

   **1** 
   **ABC**