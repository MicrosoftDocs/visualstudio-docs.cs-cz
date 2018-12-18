---
title: 'Postupy: vytvoření aplikace služeb pracovního postupu WCF | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8632d8cf942fe4a06f12d324fea1f6f567080981
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228433"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Postupy: vytvoření aplikace služeb pracovního postupu WCF
[!INCLUDE[indigo1](../includes/indigo1-md.md)] aplikace služeb pracovního postupu jsou distribuované komunikační služby, které předávání zpráv mezi klienty a sami přes hranice procesu. Implementace kontraktu služby na straně služby se provádí pomocí deklarace pomocí aktivit pracovního postupu v [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] způsobem, který je obdobou služby starší verze pracovních postupů v rozhraní .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Vytvoření aplikace služeb pracovního postupu WCF  
  
1.  Spustit [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu...** .  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  V **nainstalované šablony** vyberte **WCF** nebo **pracovního postupu** buď z **Visual C#** nebo **jazykaVisualBasic** seskupení v závislosti na jazyku podle výběru.  
  
4.  V prostředním podokně vyberte **aplikace služeb pracovního postupu WCF**.  
  
5.  V **název** zadejte popisný název pro váš projekt, aby byl snadno identifikovat.  
  
6.  V **umístění** zadejte adresář, ve kterém chcete projekt uložit, nebo klikněte na tlačítko **Procházet** přejít k němu.  
  
7.  V **řešení** vyberte vytvoření nového řešení a potom klikněte na **OK**.  
  
    > [!NOTE]
    >  Pokud chcete přidat Konzolová aplikace pracovního postupu do existujícího řešení, otevřete toto řešení [!INCLUDE[vs2010](../includes/vs2010-md.md)], klikněte pravým tlačítkem na řešení v **Průzkumníka řešení**a vyberte **přidat**, pak  **Nový projekt...** Chcete-li otevřít **nový projekt** dialogové okno. Pokračujte, jak je popsáno výše v tomto postupu.  
  
8.  Šablona projektu vytvoří definici služby jako XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Do návrhového zobrazení se otevře <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje sadu <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření aktivity](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)