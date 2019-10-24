---
title: 'Ladění ASP.NET: požadavky na systém | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 78f947c7ab9fcc1031d457526240ecdd7e9119a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745811"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Ladění: Systémové požadavky
Toto téma popisuje požadavky na software a zabezpečení pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] scénáře ladění:

- Místní ladění, ve kterém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a webová aplikace běží ve stejném počítači. Existují dvě verze tohoto scénáře:

  - Kód [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se nachází v systému souborů.

  - Kód [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se nachází na webu služby IIS.

- Vzdálené ladění, ve kterém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] běží na klientském počítači a ladí webovou aplikaci, která běží na vzdáleném počítači serveru.

## <a name="security-requirements"></a>Požadavky na zabezpečení
 Pro vzdálené ladění musí být místní a vzdálené počítače v nastavení domény nebo v pracovní skupině.

 Chcete-li ladit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces (hostovaný fondem aplikací), musíte mít oprávnění pro ladění tohoto procesu. Ve výchozím nastavení [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace před službou IIS 6,0 spustit jako uživatel **ASPNET** . Ve službě IIS 6,0 a IIS 7,0 je výchozím účtem **síťové služby** . Pokud pracovní proces běží jako **ASPNET**nebo jako **Síťová služba**, musíte mít oprávnění správce, abyste ho mohli ladit.

 > [!IMPORTANT]
 > Počínaje systémem Windows Server 2008 R2 doporučujeme použití [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako identity pro každý fond aplikací.

 Název pracovního procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se liší podle scénáře ladění a podle verze služby IIS. Další informace najdete v tématu [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 Uživatelský účet, pod kterým běží pracovní proces [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], můžete změnit úpravou souboru Machine. config na serveru, na kterém je spuštěna služba IIS. Nejlepším způsobem, jak to provést, je použít **Správce služby Internetová informační služba (IIS)** . Další informace najdete v tématu [Postup: spuštění pracovního procesu v rámci uživatelského účtu](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 Změníte-li [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces tak, aby běžel pod vlastním uživatelským účtem, nemusíte být správcem serveru, na kterém je spuštěna služba IIS.

> [!CAUTION]
> Před změnou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu tak, aby běžel pod jiným účtem, vezměte v úvahu možné důsledky v případě, že by měl být při spuštění pod tímto účtem napadený [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces. Uživatelské účty ASPNET a NETWORK SERVICE se spouštějí s minimálními oprávněními a snižují možný škodu v případě, že je proces napadený. Pokud je nutné změnit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces tak, aby běžel pod účtem, který má větší oprávnění, je potenciální Škoda větší.

## <a name="see-also"></a>Viz také:

- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Postupy: Spuštění pracovního procesu v rámci uživatelského účtu](../debugger/how-to-run-the-worker-process-under-a-user-account.md)