---
title: Prostředí ASP.NET není nainstalováno.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1c4138b1f3d102e235bb03ebcfd5a80808d8762c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852794"
---
# <a name="error-aspnet-not-installed"></a>Chyba: Prostředí ASP.NET není nainstalováno.
K této chybě dochází, pokud [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] není správně nainstalován na počítači, který se pokoušíte ladit. To může znamenat, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nebyla nikdy nainstalována nebo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] byla nainstalována dříve a služba IIS byla nainstalována později.

### <a name="to-reinstall-aspnet"></a>Postup přeinstalace ASP.NET

1. V okně příkazového řádku spusťte následující příkaz:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    kde *verze* představuje číslo verze .NET Framework nainstalovaného v počítači, například v 1.0.370. Verzi rozhraní můžete určit tak, že v adresáři prohlížíte `\WINDOWS\Microsoft.NET\Framework` .

   > [!NOTE]
   > S Windows serverem 2003 můžete nainstalovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pomocí ovládacího panelu **Přidat nebo odebrat programy** .

## <a name="see-also"></a>Viz také
- [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
