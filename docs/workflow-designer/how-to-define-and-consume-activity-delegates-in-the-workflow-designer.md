---
title: Definování a použití delegátů aktivit
description: V Návrhář postupu provádění se naučíte, jak .NET Framework 4,5 obsahuje předem připravený Návrhář pro aktivitu InvokeDelegate, kterou můžete použít k definování a využívání delegátů aktivit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 48cab69de11ce006792e0fda72245048c6897acf
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993273"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Postupy: Definování a použití delegátů aktivit v návrháři postupu provádění

.NET Framework 4,5 obsahuje předem připravený Návrhář pro <xref:System.Activities.Statements.InvokeDelegate> aktivitu. Tento návrhář lze použít k přiřazení delegátů aktivitě, která je odvozena z <xref:System.Activities.ActivityDelegate> , například <xref:System.Activities.ActivityAction> nebo <xref:System.Activities.ActivityFunc%601> .

## <a name="define-an-activity-delegate"></a>Definovat delegáta aktivity

1. Vytvořte nový projekt **konzolové aplikace pracovního postupu** .

   > [!NOTE]
   > Pokud nevidíte šablony projektu **pracovního postupu** , nainstalujte nejprve součást **programovací model Windows Workflow Foundation** sady Visual Studio. Podrobné pokyny najdete v tématu [instalace programovací model Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **novou položku**. Vyberte kategorii **pracovního postupu** a potom vyberte šablonu položka **aktivity** . Pojmenujte novou aktivitu **MyForEach. XAML** a pak vyberte **OK**.

   Aktivita se otevře v Návrháři pracovních postupů.

4. V Návrhář postupu provádění klikněte na kartu **argumenty** .

5. Klikněte na **vytvořit argument**. Pojmenujte nové **položky** argumentu.

6. Ve sloupci **typ argumentu** vyberte **pole z [T]**.

7. V prohlížeči typů vyberte **objekt** a pak vyberte **OK**.

8. Znovu klikněte na tlačítko **vytvořit argument** . Pojmenujte nový **hlavní část** argumentu. Ve sloupci **směr** pro nový argument vyberte **vlastnost**.

9. Ve sloupci Typ argumentu vyberte **Vyhledat typy** .

10. V prohlížeči typu zadejte **ActivityAction** do pole **název typu** . Ve stromovém zobrazení vyberte **ActivityAction \<T>** . V rozevíracím seznamu vyberte **objekt** , který se zobrazí, chcete-li typ **ActivityAction \<Object>** přiřadit k argumentu.

11. Přetáhněte <xref:System.Activities.Statements.While> aktivitu z části **tok řízení** v sadě nástrojů na plochu návrháře.

12. Vyberte <xref:System.Activities.Statements.While> aktivitu a vyberte kartu **proměnné** .

13. Vyberte **vytvořit proměnnou**. Pojmenujte nový **index** proměnné.

14. Ve sloupci **typ proměnné** vyberte **Int32**. Tento **obor** ponechte jako **while** a **výchozí** sloupec je prázdný.

15. Nastavte vlastnost **Condition** <xref:System.Activities.Statements.While> aktivity na **index < položky. Length;**.

16. Přetáhněte <xref:System.Activities.Statements.InvokeDelegate> aktivitu z oddílu **primitivs** v sadě nástrojů na **tělo** <xref:System.Activities.Statements.While> aktivity.

17. V rozevíracím seznamu delegáta vyberte **text** .

18. V mřížce **vlastnosti** <xref:System.Activities.Statements.InvokeDelegate> aktivity klikněte na tlačítko **...** ve vlastnosti **argumenty delegátů** .

19. Do sloupce **hodnota** argumentu pojmenovaného **argumentu** zadejte **Items [index]**. Kliknutím na tlačítko **OK** zavřete dialogové okno **DelegateArguments** .

20. Přetáhněte <xref:System.Activities.Statements.Assign> aktivitu na vodorovnou čáru pod <xref:System.Activities.Statements.InvokeDelegate> aktivitou. <xref:System.Activities.Statements.Assign>Aktivita se vytvoří a <xref:System.Activities.Statements.Sequence> automaticky se vytvoří aktivita, která bude obsahovat dvě aktivity v části **tělo** aktivity **MyForEach** . Sekvence je nutná, protože oddíl **body** může obsahovat pouze jednu aktivitu. Automatické vytvoření nové <xref:System.Activities.Statements.Sequence> aktivity je nová funkce .NET Framework 4,5.

21. Nastavte vlastnost **Property** <xref:System.Activities.Statements.Assign> aktivity na **index**. Nastavte vlastnost **Value** aktivity **přiřadit** na **index + 1**.

    Vlastní aktivita **MyForEach** vyvolá libovolnou aktivitu jednou pro každou předanou hodnotu prostřednictvím kolekce **Items** s hodnotami v kolekci jako vstupy pro aktivitu.

## <a name="use-the-custom-activity-in-a-workflow"></a>Použití vlastní aktivity v pracovním postupu

1. Sestavte projekt stisknutím **kombinace kláves CTRL** + **SHIFT** + **B**.

2. V **Průzkumník řešení** otevřete **Workflow1. XAML** v návrháři.

3. Přetáhněte aktivitu **MyForEach** ze sady nástrojů na plochu návrháře. Aktivita je v části sady nástrojů se stejným názvem jako projekt.

4. Nastavte vlastnost **Items** aktivity **MyForEach** na **New Object [] {1, "ABC"}**.

5. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu z oddílu **primitivs** v sadě nástrojů do části **Delegate: body** aktivity **MyForEach** .

6. Nastavte vlastnost **text** <xref:System.Activities.Statements.WriteLine> aktivity na **argument. ToString ()**.

Při spuštění pracovního postupu zobrazí Konzola následující výstup:

**1** 
 **ABC**
