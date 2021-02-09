---
title: Krokovat se službami WCF | Microsoft Docs
description: Proveďte krok do služby Windows Communication Foundation (WCF). Pokud je ve stejném řešení sady Visual Studio jako klient, volání ve službě WCF se zarážkami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f3a884698586cdd9a89ff62a090f02af3953a91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896631"
---
# <a name="how-to-step-into-wcf-services"></a>Postupy: Krokování s vnořením služeb WCF
V aplikaci [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] můžete vstoupit do služby WCF. Pokud je služba WCF ve stejném [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] řešení jako klient, můžete ve službě WCF narazit zarážky.

 Pro krokování v práci je nutné povolit ladění v souboru app.config nebo Web.config. Informace o tom, jak povolit ladění a omezení pro krokování služby WCF, najdete v tématu [omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Postup pro krokování se službou WCF

1. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] řešení, které obsahuje projekt WCF i projekty služby WCF.

2. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt klienta WCF a pak klikněte na **nastavit jako spouštěný projekt**.

3. Povolit ladění v souboru app.config nebo web.config. Další informace najdete v tématu [omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).

4. Nastavte zarážku v umístění v klientském projektu, kde chcete začít s krokování. Obvykle to bude těsně před voláním služby WCF.

5. Spusťte ke zarážce a pak začněte krokování. Ladicí program se automaticky přeskočí na službu.

## <a name="see-also"></a>Viz také
- [Ladění služeb WCF](../debugger/debugging-wcf-services.md)
- [Omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md)
- [Postupy: Ladění služby WCF s vlastním hostováním](../debugger/how-to-debug-a-self-hosted-wcf-service.md)