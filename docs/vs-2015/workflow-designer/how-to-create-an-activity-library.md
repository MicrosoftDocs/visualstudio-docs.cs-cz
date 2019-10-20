---
title: 'Postupy: Vytvoření knihovny aktivit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662747"
---
# <a name="how-to-create-an-activity-library"></a>Postupy: Vytvoření knihovny aktivit
Vlastní aktivity se používají k modelování konkrétních obchodních procesů v pracovním postupu. K dispozici je šablona knihovny aktivit v [!INCLUDE[vs2010](../includes/vs2010-md.md)], která vám umožní vytvářet takové vlastní aktivity vizuálně pomocí [!INCLUDE[wfd1](../includes/wfd1-md.md)].

### <a name="to-create-a-workflow-activity-library"></a>Vytvoření knihovny aktivit pracovního postupu

1. Spusťte [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt...** .

     Otevře se dialogové okno **Nový projekt** .

3. V podokně **typy projektů** vyberte **pracovní postup** z **vizuálních C#**  projektů nebo skupin **Visual Basic** v závislosti na jazykové předvolbách.

4. V podokně **šablony** vyberte **Knihovna aktivit**.

5. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

6. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

7. Do pole **řešení** zadejte popisný název vašeho řešení a pak klikněte na **OK**.

    > [!NOTE]
    > Pokud chcete přidat konzolovou aplikaci pracovního postupu do existujícího řešení, otevřete toto řešení v [!INCLUDE[vs2010](../includes/vs2010-md.md)], klikněte pravým tlačítkem na řešení v **Průzkumník řešení**a vyberte **Přidat**a **Nový projekt...** pro otevření dialogového okna **Nový projekt** . Pokračujte postupem uvedeným výše v tomto postupu.

8. Šablona projektu vytvoří definici aktivity v jazyce XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] se otevře a zobrazí plátno pro vaši vlastní aktivitu.

9. Přetáhněte aktivitu ze **sady nástrojů** na návrhovou plochu, aby byla zahrnuta do vlastní aktivity.

    > [!CAUTION]
    > V těle vlastní aktivity máte povolenou jenom jednu podřízenou aktivitu. tato podřízená aktivita ale může být složená aktivita, například aktivita <xref:System.Activities.Statements.Sequence> nebo aktivita <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Viz také
 [Postupy: vytvoření aktivity](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)