---
title: Doporučené postupy pro zabezpečení v balíčcích VSPackages | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709909"
---
# <a name="best-practices-for-security-in-vspackages"></a>Doporučené postupy pro zabezpečení v Balíčcích VSPackages
Chcete-li [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nainstalovat počítač, musíte být spuštěnv kontextu s pověřeními pro správu. Základní jednotkou zabezpečení a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nasazení aplikace je [VSPackage](../../extensibility/internals/vspackages.md). VSPackage musí být registrovánpomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], která také vyžaduje pověření pro správu.

 Správci mají úplná oprávnění k zápisu do registru a systému souborů a ke spuštění libovolného kódu. Musíte mít tato oprávnění k vývoji, nasazení nebo instalaci VSPackage.

 Jakmile je nainstalován, VSPackage je plně důvěryhodný. Z důvodu této vysoké úrovně oprávnění spojené s VSPackage, je možné neúmyslně nainstalovat VSPackage, který má škodlivý záměr.

 Uživatelé by měli zajistit, že instalují VSPackages pouze z důvěryhodných zdrojů. Společnosti vyvíjející VSPackages by měly důrazně pojmenovat a podepsat je, aby se ujistil uživatele, že je zabráněno manipulaci. Společnosti vyvíjející vSPackages by měly prozkoumat své externí závislosti, jako jsou webové služby a vzdálená instalace, aby vyhodnotily a opravily všechny problémy se zabezpečením.

 Další informace naleznete [v tématu Bezpečné kódování pokyny pro rozhraní .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Viz také
- [Zabezpečení doplňku](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Zabezpečení DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
