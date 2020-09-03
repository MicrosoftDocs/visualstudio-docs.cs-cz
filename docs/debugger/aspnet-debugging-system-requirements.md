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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745811"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Ladění: Systémové požadavky
Toto téma popisuje požadavky na software a zabezpečení pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] scénáře ladění:

- Místní ladění, ve kterém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a webová aplikace běží ve stejném počítači. Existují dvě verze tohoto scénáře:

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Kód se nachází v systému souborů.

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Kód se nachází na webu služby IIS.

- Vzdálené ladění, ve kterém se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spouští na klientském počítači a ladí webovou aplikaci, která běží na vzdáleném počítači serveru.

## <a name="security-requirements"></a>Požadavky na zabezpečení
 Pro vzdálené ladění musí být místní a vzdálené počítače v nastavení domény nebo v pracovní skupině.

 Chcete-li ladit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces (hostovaný fondem aplikací), musíte mít oprávnění pro ladění tohoto procesu. Ve výchozím nastavení se [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace před IIS 6,0 spouštějí jako uživatel **ASPNET** . Ve službě IIS 6,0 a IIS 7,0 je výchozím účtem **síťové služby** . Pokud pracovní proces běží jako **ASPNET**nebo jako **Síťová služba**, musíte mít oprávnění správce, abyste ho mohli ladit.

 > [!IMPORTANT]
 > Počínaje systémem Windows Server 2008 R2 doporučujeme použití [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako identity pro každý fond aplikací.

 Název [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu se liší podle scénáře ladění a podle verze služby IIS. Další informace najdete v tématu [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 Uživatelský účet, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pod kterým běží pracovní proces, můžete změnit úpravou machine.config souboru na serveru, na kterém je spuštěna služba IIS. Nejlepším způsobem, jak to provést, je použít **Správce služby Internetová informační služba (IIS)**. Další informace najdete v tématu [Postup: spuštění pracovního procesu v rámci uživatelského účtu](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 Pokud změníte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces tak, aby běžel pod vlastním uživatelským účtem, nemusíte být správcem serveru, na kterém je spuštěna služba IIS.

> [!CAUTION]
> Před změnou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu tak, aby běžel pod jiným účtem, zvažte možné důsledky v případě, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] by měl být při spuštění pod tímto účtem napadený pracovní proces. Uživatelské účty ASPNET a NETWORK SERVICE se spouštějí s minimálními oprávněními a snižují možný škodu v případě, že je proces napadený. Pokud je potřeba změnit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces tak, aby běžel pod účtem, který má větší oprávnění, je potenciální Škoda větší.

## <a name="see-also"></a>Viz také

- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Postupy: spuštění pracovního procesu v rámci uživatelského účtu](../debugger/how-to-run-the-worker-process-under-a-user-account.md)