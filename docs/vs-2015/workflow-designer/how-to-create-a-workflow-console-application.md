---
title: 'Postupy: vytvoření konzolové aplikace pracovního postupu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ad509e0e57f2c8996c13ffbe1d8f8890d2954dec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251664"
---
# <a name="how-to-create-a-workflow-console-application"></a>Postupy: vytvoření konzolové aplikace pracovního postupu
[!INCLUDE[wf](../includes/wf-md.md)] umožňuje vytvářet pracovní postupy pro spouštění systému nebo lidské procesy. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Poskytuje na návrhovou plochu pro vytváření těchto pracovních postupů. [!INCLUDE[wfd2](../includes/wfd2-md.md)] Slouží k vytváření pracovních postupů v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo je možné integrovat do jiných aplikací, které změna hostitele návrháře.  
  
 Toto téma popisuje způsob použití [!INCLUDE[wfd2](../includes/wfd2-md.md)] v [!INCLUDE[vs2010](../includes/vs2010-md.md)] vytvoření pracovního postupu v konzolové aplikaci.  
  
### <a name="to-create-a-workflow-console-application"></a>K vytvoření konzolové aplikace pracovního postupu  
  
1.  Spustit [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu...** .  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  V **nainstalované šablony** vyberte **pracovního postupu** buď z **Visual C#** nebo **jazyka Visual Basic** seskupení, v závislosti na vaší jazykové předvolby.  
  
4.  V prostředním podokně vyberte **Konzolová aplikace pracovního postupu**.  
  
5.  V **název** zadejte popisný název pro váš projekt, aby byl snadno identifikovat.  
  
6.  V **umístění** zadejte adresář, ve kterém chcete projekt uložit, nebo klikněte na tlačítko **Procházet** přejít k němu.  
  
7.  V **řešení** pole, zadejte název nového řešení. Klikněte na tlačítko **OK** k vytvoření aplikace.  
  
    > [!NOTE]
    >  Pokud chcete přidat Konzolová aplikace pracovního postupu do existujícího řešení, otevřete toto řešení [!INCLUDE[vs2010](../includes/vs2010-md.md)], klikněte pravým tlačítkem na řešení v **Průzkumníka řešení**a vyberte **přidat**, pak  **Nový projekt...** Chcete-li otevřít **nový projekt** dialogové okno. Pokračujte, jak je popsáno výše v tomto postupu.  
  
8.  Šablona projektu vytvoří definici pracovního postupu v XAML a definice aplikace konzoly je ve zdrojovém kódu. [!INCLUDE[wfd2](../includes/wfd2-md.md)] Se otevře a zobrazí na plátně pro pracovní postup, který jste vytvořili.  
  
9. K vytvoření pracovního postupu, přetáhněte aktivity nebo jiné položky pracovního postupu z **nástrojů** na návrhovou plochu v pracovním postupu.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)