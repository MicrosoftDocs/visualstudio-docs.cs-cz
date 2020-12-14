---
title: Ladění služby Self-Hosted WCF | Microsoft Docs
Description: Naučte se ladit službu WCF s místním hostováním. Nejjednodušší způsob (ale ne vždy možný) je konfigurace sady Visual Studio tak, aby spouštěla klienta i server.
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
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983c053ca6bd1370cf67cb04eeb2626c2b1217aa
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398724"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Postupy: Ladění služby WCF s vlastním hostováním
*Samoobslužná služba* je služba WCF, která neběží ve službě IIS, hostiteli služby WCF ani [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vývojovém serveru. Nejjednodušší způsob, jak ladit technologii WCF v místním prostředí, je nakonfigurovat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tak, aby spouštěla klienta i server, když zvolíte možnost **Spustit ladění** v nabídce **ladění** .

 Tuto metodu nelze použít, pokud je služba WCF s vlastním hostováním uvnitř procesu, který nelze spustit tímto způsobem, jako je služba NT. Místo toho lze provést jednu z následujících možností:

- Ladicí program k hostitelskému procesu připojit ručně. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     ani

- Spustit ladění klientu a poté krokovat s vnořením volání služby. To vyžaduje povolení ladění v souboru app.config. Další informace najdete [v omezeních pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Spuštění klientu a hostitele v systému Visual Studio

1. Vytvořte řešení systému [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], které obsahuje projekty klientu i serveru.

2. Nakonfigurujte řešení tak, aby spouštělo procesy klienta i serveru, když v nabídce **ladění** zvolíte možnost **Spustit** .

   1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na název řešení.

   2. Klikněte na **nastavit projekty po spuštění**.

   3. V dialogovém **okně \<name> vlastnosti řešení** vyberte **více projektů po spuštění**.

   4. V mřížce **vícenásobné spouštěné projekty** na řádku, který odpovídá projektu serveru, klikněte na tlačítko **Akce** a vyberte možnost **Spustit**.

   5. Na řádku, který odpovídá projektu klienta, klikněte na tlačítko **Akce** a vyberte možnost **Spustit**.

   6. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
- [Ladění služeb WCF](../debugger/debugging-wcf-services.md)
- [Omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md)
- [Postupy: krokování se službami WCF](../debugger/how-to-step-into-wcf-services.md)