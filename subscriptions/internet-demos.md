---
title: Použití kódů Product Key k podpoře internetových předvádění prostřednictvím Terminálové služby | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/09/2020
ms.topic: conceptual
description: Naučte se používat kódy Product Key k podpoře internetových ukázek prostřednictvím Terminálové služby a povolit přístup rds
ms.openlocfilehash: 2d5f23f0d161ee9f50569e0ff7f8ce585c8c49ff
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232432"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Internetové demonstrace prostřednictvím Terminálové služby
S předplatným sady Visual Studio můžete koncovým uživatelům poskytovat přístup k internetovým ukázkám programů prostřednictvím Terminálové služby (Windows Server 2003 nebo Windows Server 2008) nebo Služby vzdálené plochy (Windows Server 2008 R2 a novější). Tímto způsobem může k vaší demonstraci současně přistupovat až 200 anonymních uživatelů. Ukázka nesmí používat produkční data. Předplatitelé sady Visual Studio mají licenci k předvádění svých aplikací koncovým uživatelům. Tato internetová ukázka pomocí Terminálové služby (TS) nebo vzdálené služby vzdálené plochy (RDS) je jediným scénářem, kdy koncoví uživatelé bez předplatného sady Visual Studio mohou pracovat s demonstrační aplikací, pokud je software licencován prostřednictvím aplikace Visual Studio předplatná.

Toto je kromě práva na vývoj a testování, kde předplatitelé sady Visual Studio můžete použít tolik připojení RDS nebo TS podle potřeby.

## <a name="enabling-rds-access"></a>Povolení přístupu k rds
Předplatitelé sady Visual Studio mohou zvýšit počet uživatelů, kteří mají přístup k systému Windows Server prostřednictvím služby RDS, zadáním kódu Product Key dodaného na kartě [Kódy Product Key](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) na [portálu odběratelů](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Chcete-li získat kód Product Key, připojte se ke stránce Product Key a přejděte dolů na verzi systému Windows Server, kterou používáte. Vyhledejte "Windows Server < verze > Vzdálené plochy R2 < uživatelem nebo připojením zařízení > připojení" a klepněte na odkaz **Klíč deklarace.** Pokud například používáte službu RdS v systému Windows Server 2012 R2 a vaše nasazení používá licence CA, zvolte možnost "Připojení uživatelů služby Vzdálená plocha systému Windows Server 2012 (50)".
Pro systém Windows Server 2008 R2 je k dispozici pět klíčů každého typu a každý klíč bude podporovat 20 připojení. Pro systém Windows Server 2012 R2 jsou čtyři klíče pro každý typ poskytovat a bude podporovat 50 připojení každý.

## <a name="to-enable-additional-connections-in-windows-server"></a>Povolení dalších připojení v systému Windows Server:
1. Spusťte Správce serveru.
2. Otevřete seznam Servery v levém navigačním podokně.
3. Klikněte pravým tlačítkem myši na licenční server a zvolte "Instalovat licence".
4. Postupujte podle pokynů průvodce.  Při výběru typu smlouvy zvolte "License Pack (maloobchod)" a zadejte kód Product Key, který jste získali z portálu MY.

Koncoví uživatelé se mohou připojit k přístupovým aplikacím prostřednictvím služby RDS, pokud jsou splněny následující podmínky:
- Uživatelé musí být anonymní (v neověřeném stavu).
- Připojení musí být přes Internet.
- Pro ukázky aplikace lze použít až 200 souběžných uživatelských připojení.
- Kódy Product Key umožňující připojení uživatelů musí získat předplatitel e-sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Documenation systému Windows Server](https://docs.microsoft.com/windows-server/)
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Pokud potřebujete pokyny pro nasazení rds, podívejte se na vícedílné blogové řady na nasazení https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerfrelace Vzdálené plochy **(RDS) 2012** na . 

Máte-li jakékoli dotazy, navštivte [fórum služby Vzdálená plocha společnosti Microsoft](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
