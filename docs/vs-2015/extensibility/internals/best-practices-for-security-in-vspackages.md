---
title: Osvědčené postupy pro zabezpečení v VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697272"
---
# <a name="best-practices-for-security-in-vspackages"></a>Osvědčené postupy pro zabezpečení v balíčcích VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chcete-li nainstalovat aplikaci do [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] počítače, je nutné, abyste byli spuštěni v kontextu s pověřením správce. Základní jednotkou zabezpečení a nasazení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aplikace jsou sady [VSPackage](../../extensibility/internals/vspackages.md). VSPackage musí být registrován pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , který také vyžaduje pověření správce.  
  
 Správci mají úplná oprávnění k zápisu do registru a systému souborů a pro spuštění libovolného kódu. Musíte mít tato oprávnění pro vývoj, nasazení nebo instalaci VSPackage.  
  
 Jakmile je nainstalován, VSPackage je plně důvěryhodný. Z důvodu této vysoké úrovně oprávnění přidruženého k VSPackage je možné nechtěně nainstalovat VSPackage, který má škodlivý záměr.  
  
 Uživatelé by měli mít jistotu, že budou instalovat VSPackage jenom z důvěryhodných zdrojů. Společnosti vyvíjející VSPackage by se měly silně pojmenovat a podepisovat, aby zajistily, že uživatel brání manipulaci. Společnosti, které vyvíjí VSPackage, by měli prošetřit své externí závislosti, jako jsou webové služby a Vzdálená instalace, a vyhodnocovat a opravovat případné problémy se zabezpečením.  
  
 Další informace najdete v tématu pokyny k zabezpečenému kódování pro .NET Framework ( [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) ).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení doplňku](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Zabezpečení DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
