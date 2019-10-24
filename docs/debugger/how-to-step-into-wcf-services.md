---
title: 'Postupy: krokování se službami WCF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c405b4fcca91f8deddce4d65c8a4155b90af49e0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732601"
---
# <a name="how-to-step-into-wcf-services"></a>Postupy: Krokování s vnořením služeb WCF
V [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] můžete vstoupit do služby WCF. Pokud je služba WCF ve stejném řešení [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jako klient nástroje, můžete ve službě WCF narazit zarážky.

 Pro krokování v práci je nutné povolit ladění v souboru App. config nebo Web. config. Informace o tom, jak povolit ladění a omezení pro krokování služby WCF, najdete v tématu [omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Postup pro krokování se službou WCF

1. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] řešení, které obsahuje projekty WCF i služby WCF.

2. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt klienta WCF a pak klikněte na **nastavit jako spouštěný projekt**.

3. Povolte ladění v souboru App. config nebo Web. config. Další informace najdete v tématu [omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).

4. Nastavte zarážku v umístění v klientském projektu, kde chcete začít s krokování. Obvykle to bude těsně před voláním služby WCF.

5. Spusťte ke zarážce a pak začněte krokování. Ladicí program se automaticky přeskočí na službu.

## <a name="see-also"></a>Viz také:
- [Ladění služeb WCF](../debugger/debugging-wcf-services.md)
- [Omezení ladění WCF](../debugger/limitations-on-wcf-debugging.md)
- [Postupy: Ladění služby WCF s vlastním hostováním](../debugger/how-to-debug-a-self-hosted-wcf-service.md)