---
title: 'Postupy: vyvolání operace kontraktu Windows Communication Foundation (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603705"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Postupy: vyvolání operace kontraktu Windows Communication Foundation (starší verze)
Toto téma popisuje, jak vyvolat operaci [!INCLUDE[indigo1](../includes/indigo1-md.md)] kontraktu pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)], která cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Po přetažení aktivity **SendActivity** ze sady nástrojů na návrhovou plochu pracovního postupu je nutné naimportovat stávající kontrakt a určit, která operace bude z dané aktivity **SendActivity** vyvolána. Svůj kontrakt a jeho operace můžete vybrat v [dialogovém okně zvolte operaci (starší verze)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Pokud používáte konfigurační soubor s vaší službou, budete muset zadat <xref:System.Workflow.Activities.ChannelToken>. @No__t_0 identifikuje konfiguraci koncového bodu, kterou vaše aktivita odeslání používá pro připojení ke službě pracovního postupu.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Postup vyvolání operace kontraktu WCF z aktivity SendActivity

1. Dvakrát klikněte na aktivitu **SendActivity** v Návrháři nebo klikněte na tři tečky vedle vlastnosti **ServiceOperationInfo** v podokně **vlastnosti** .

2. Po otevření dialogového okna **Zvolit operaci** klikněte na **importovat** v pravém horním rohu dialogového okna.

     Otevře se [dialogové okno Procházet a vybrat typ .NET (starší verze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) .

3. Vyhledejte sestavení nebo projekt, které obsahují kontrakt, který chcete.

4. Vyberte kontrakt a klikněte na **OK**.

5. V části **dostupné operace**vyberte operaci, kterou chcete vyvolat, a klikněte na **OK**.

### <a name="to-specify-a-channel-token"></a>Určení tokenu kanálu

1. V návrháři vyberte aktivitu <xref:System.Workflow.Activities.SendActivity>.

2. V podokně **vlastnosti** zadejte název <xref:System.Workflow.Activities.ChannelToken>. Tento název jednoznačně identifikuje token kanálu.

3. Rozbalte uzel token kanálu a zadejte název koncového bodu klienta, který budete používat v poli <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. Konfigurace koncového bodu se stejným názvem v konfiguračním souboru se použije ke konfiguraci kanálu.

4. Vytvořte konfiguraci koncového bodu v konfiguračním souboru, pokud již neexistuje. Další informace o konfiguraci klienta najdete v tématu [Přehled klientů WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Viz také
 [Výběr operace – dialogové okno (starší verze)](../workflow-designer/choose-operation-dialog-box-legacy.md) [Postupy: implementace operace kontraktu WCF (starší verze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [starší aktivity pracovního postupu](../workflow-designer/legacy-workflow-activities.md)