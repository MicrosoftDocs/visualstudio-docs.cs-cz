---
title: Osvědčené postupy pro zabezpečení v VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e73be2af3d24a6a719f353fbd0ab25dbdf86fe09
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012136"
---
# <a name="best-practices-for-security-in-vspackages"></a>Osvědčené postupy pro zabezpečení v VSPackage
Chcete-li nainstalovat aplikaci do [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] počítače, je nutné, abyste byli spuštěni v kontextu s pověřením správce. Základní jednotkou zabezpečení a nasazení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikace je [VSPackage](../../extensibility/internals/vspackages.md). VSPackage musí být registrován pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , který také vyžaduje pověření správce.

 Správci mají úplná oprávnění k zápisu do registru a systému souborů a pro spuštění libovolného kódu. Musíte mít tato oprávnění pro vývoj, nasazení nebo instalaci VSPackage.

 Jakmile je nainstalován, VSPackage je plně důvěryhodný. Z důvodu této vysoké úrovně oprávnění přidruženého k VSPackage je možné nechtěně nainstalovat VSPackage, který má škodlivý záměr.

 Uživatelé by měli mít jistotu, že budou instalovat VSPackage jenom z důvěryhodných zdrojů. Společnosti vyvíjející VSPackage by se měly silně pojmenovat a podepisovat, aby zajistily, že uživatel brání manipulaci. Společnosti, které vyvíjí VSPackage, by měli prošetřit své externí závislosti, jako jsou webové služby a Vzdálená instalace, a vyhodnocovat a opravovat případné problémy se zabezpečením.

 Další informace najdete v tématu [pokyny k zabezpečenému kódování pro .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Viz také:
- [Zabezpečení doplňku](/previous-versions/1326zbk3(v=vs.140))
- [Zabezpečení DDEX](/previous-versions/bb163703(v=vs.140))