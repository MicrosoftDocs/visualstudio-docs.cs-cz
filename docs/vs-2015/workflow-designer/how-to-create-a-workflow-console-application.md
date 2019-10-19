---
title: 'Postupy: Vytvoření konzolové aplikace pracovního postupu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604922"
---
# <a name="how-to-create-a-workflow-console-application"></a>Postupy: Vytvoření konzolové aplikace pracovního postupu
[!INCLUDE[wf](../includes/wf-md.md)] umožňuje vytvářet pracovní postupy pro provádění systémových nebo lidských procesů. @No__t_0 poskytuje návrhovou plochu pro vytváření těchto pracovních postupů. @No__t_0 lze použít k vytvoření pracovních postupů v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo je lze integrovat do jiných aplikací, které rehostují návrháře.

 Toto téma popisuje, jak použít [!INCLUDE[wfd2](../includes/wfd2-md.md)] v [!INCLUDE[vs2010](../includes/vs2010-md.md)] k vytvoření pracovního postupu v konzolové aplikaci.

### <a name="to-create-a-workflow-console-application"></a>Vytvoření konzolové aplikace pracovního postupu

1. Spusťte [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt...** .

     Otevře se dialogové okno **Nový projekt** .

3. V podokně **Nainstalované šablony** vyberte v závislosti na vašem jazyce předvolby **pracovní postup** ze seskupení  **C# vizuálů** nebo **Visual Basic** .

4. V prostředním podokně vyberte **Konzolová aplikace pracovního postupu**.

5. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

6. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

7. Do pole **řešení** zadejte název nového řešení. Kliknutím na tlačítko **OK** vytvořte aplikaci.

    > [!NOTE]
    > Pokud chcete přidat konzolovou aplikaci pracovního postupu do existujícího řešení, otevřete toto řešení v [!INCLUDE[vs2010](../includes/vs2010-md.md)], klikněte pravým tlačítkem na řešení v **Průzkumník řešení**a vyberte **Přidat**a **Nový projekt...** pro otevření dialogového okna **Nový projekt** . Pokračujte postupem uvedeným výše v tomto postupu.

8. Šablona projektu vytvoří definici pracovního postupu v jazyce XAML a definice konzolové aplikace je ve zdrojovém kódu. @No__t_0 se otevře a zobrazí plátno pro pracovní postup, který jste vytvořili.

9. Chcete-li vytvořit pracovní postup, přetáhněte aktivity nebo jiné položky pracovního postupu ze **sady nástrojů** na návrhovou plochu pracovního postupu.

## <a name="see-also"></a>Viz také
 [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)