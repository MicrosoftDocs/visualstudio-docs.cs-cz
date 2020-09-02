---
title: 'Chyba: ASP.NET není nainstalován | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64823732"
---
# <a name="error-aspnet-not-installed"></a>Chyba: Prostředí ASP.NET není nainstalováno.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K této chybě dochází, pokud [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] není správně nainstalován na počítači, který se pokoušíte ladit. To může znamenat, že [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nebyla nikdy nainstalována nebo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] byla nainstalována dříve a služba IIS byla nainstalována později.  
  
### <a name="to-reinstall-aspnet"></a>Postup přeinstalace ASP.NET  
  
1. V okně příkazového řádku spusťte následující příkaz:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     kde *verze* představuje číslo verze .NET Framework nainstalovaného v počítači, například v 1.0.370. Verzi rozhraní můžete určit tak, že v adresáři prohlížíte `\WINDOWS\Microsoft.NET\Framework` .  
  
    > [!NOTE]
    > S Windows serverem 2003 můžete nainstalovat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pomocí ovládacího panelu **Přidat nebo odebrat programy** .  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
