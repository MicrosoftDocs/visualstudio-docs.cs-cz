---
title: 'Návrhář postupu provádění: definování a používání delegátů aktivit'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 67e862e3772b157c4a0999ccd44c3698119ae8a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650340"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Postupy: definice a využívání delegátů aktivit v Návrhář postupu provádění

.NET Framework 4,5 obsahuje předem připravený Návrhář pro aktivitu <xref:System.Activities.Statements.InvokeDelegate>. Tento návrhář lze použít k přiřazení delegátů aktivitě, která je odvozena od <xref:System.Activities.ActivityDelegate>, například <xref:System.Activities.ActivityAction> nebo <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definovat delegáta aktivity

1. Vytvořte nový projekt **konzolové aplikace pracovního postupu** .

   > [!NOTE]
   > Pokud nevidíte šablony projektu **pracovního postupu** , nainstalujte nejprve součást **programovací model Windows Workflow Foundation** sady Visual Studio. Podrobné pokyny najdete v tématu [instalace programovací model Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **Přidat**  > **Nová položka**. Vyberte kategorii **pracovního postupu** a potom vyberte šablonu položka **aktivity** . Pojmenujte novou aktivitu **MyForEach. XAML** a pak vyberte **OK**.

   Aktivita se otevře v Návrháři pracovních postupů.

4. V Návrhář postupu provádění klikněte na kartu **argumenty** .

5. Klikněte na **vytvořit argument**. Pojmenujte nové **položky**argumentu.

6. Ve sloupci **typ argumentu** vyberte **pole z [T]** .

7. V prohlížeči typů vyberte **objekt** a pak vyberte **OK**.

8. Znovu klikněte na tlačítko **vytvořit argument** . Pojmenujte nový **hlavní část**argumentu. Ve sloupci **směr** pro nový argument vyberte **vlastnost**.

9. Ve sloupci Typ argumentu vyberte **Vyhledat typy** .

10. V prohlížeči typu zadejte **ActivityAction** do pole **název typu** . Ve stromovém zobrazení vyberte **ActivityAction \<T >** . V rozevíracím seznamu vyberte **objekt** , který se zobrazí, **\<Object >** k argumentu přiřadit typ ActivityAction.

11. Přetáhněte aktivitu <xref:System.Activities.Statements.While> z části **Flow řízení** v sadě nástrojů na plochu návrháře.

12. Vyberte aktivitu <xref:System.Activities.Statements.While> a vyberte kartu **proměnné** .

13. Vyberte **vytvořit proměnnou**. Pojmenujte nový **index**proměnné.

14. Ve sloupci **typ proměnné** vyberte **Int32**. Tento **obor** ponechte jako **while**a **výchozí** sloupec je prázdný.

15. Nastavte vlastnost **Condition** aktivity <xref:System.Activities.Statements.While> tak, aby **< položky indexována. délka;** .

16. Přetáhněte aktivitu <xref:System.Activities.Statements.InvokeDelegate> z oddílu **primitivs** v sadě nástrojů na **tělo** aktivity <xref:System.Activities.Statements.While>.

17. V rozevíracím seznamu delegáta vyberte **text** .

18. V mřížce **vlastnosti** aktivity <xref:System.Activities.Statements.InvokeDelegate> klikněte na tlačítko **...** ve vlastnosti **argumenty delegáta** .

19. Do sloupce **hodnota** argumentu pojmenovaného **argumentu**zadejte **Items [index]** . Kliknutím na tlačítko **OK** zavřete dialogové okno **DelegateArguments** .

20. Přetáhněte aktivitu <xref:System.Activities.Statements.Assign> na vodorovnou čáru pod aktivitou <xref:System.Activities.Statements.InvokeDelegate>. Vytvoří se aktivita <xref:System.Activities.Statements.Assign> a automaticky se vytvoří aktivita <xref:System.Activities.Statements.Sequence>, která bude obsahovat dvě aktivity v části **tělo** aktivity **MyForEach** . Sekvence je nutná, protože oddíl **body** může obsahovat pouze jednu aktivitu. Automatické vytvoření nové aktivity <xref:System.Activities.Statements.Sequence> je nová funkce .NET Framework 4,5.

21. Nastavte vlastnost **Property aktivity <xref:System.Activities.Statements.Assign> na** **index**. Nastavte vlastnost **Value** aktivity **přiřadit** na **index + 1**.

    Vlastní aktivita **MyForEach** vyvolá libovolnou aktivitu jednou pro každou předanou hodnotu prostřednictvím kolekce **Items** s hodnotami v kolekci jako vstupy pro aktivitu.

## <a name="use-the-custom-activity-in-a-workflow"></a>Použití vlastní aktivity v pracovním postupu

1. Sestavte projekt stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**.

2. V **Průzkumník řešení**otevřete **Workflow1. XAML** v návrháři.

3. Přetáhněte aktivitu **MyForEach** ze sady nástrojů na plochu návrháře. Aktivita je v části sady nástrojů se stejným názvem jako projekt.

4. Nastavte vlastnost **Items** aktivity **MyForEach** na **New Object [] {1, "ABC"}** .

5. Přetáhněte aktivitu <xref:System.Activities.Statements.WriteLine> z oddílu **primitivs** v sadě nástrojů do oddílu **Delegate: body** aktivity **MyForEach** .

6. Nastavte vlastnost **text** aktivity <xref:System.Activities.Statements.WriteLine> na **argument. ToString ()** .

Při spuštění pracovního postupu zobrazí Konzola následující výstup:

**1** 
**ABC**