---
title: 'Chyba: ASP.NET není nainstalován | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 7d754cc2bb7931cdcbdb42abeddd554390ba320c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737909"
---
# <a name="error-aspnet-not-installed"></a>Chyba: Prostředí ASP.NET není nainstalováno.
K této chybě dochází, pokud [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] není správně nainstalován na počítači, který se pokoušíte ladit. To může znamenat, že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nikdy nebyl nainstalován nebo že [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] byl nainstalován jako první a služba IIS byla nainstalována později.

### <a name="to-reinstall-aspnet"></a>Postup přeinstalace ASP.NET

1. V okně příkazového řádku spusťte následující příkaz:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    kde *verze* představuje číslo verze .NET Framework nainstalovaného v počítači, například v 1.0.370. Verzi rozhraní můžete určit tak, že prohlížíte adresář `\WINDOWS\Microsoft.NET\Framework`.

   > [!NOTE]
   > S Windows serverem 2003 můžete nainstalovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pomocí ovládacího panelu **Přidat nebo odebrat programy** .

## <a name="see-also"></a>Viz také:
- [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
