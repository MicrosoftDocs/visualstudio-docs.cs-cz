---
title: 'Chyba: Ladění ve smíšeném režimu je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 2.0 nebo vyšší | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 992bd5be3f0db0ffc560d8479e6c7142c20bf031
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880153"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Chyba: Ladění ve smíšeném režimu je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 2.0 nebo vyšší.
Chcete-li ladit smíšené nativního a spravovaného kódu, musíte mít [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verze 2.0, 3.0. 3.5 nebo 4.0. Ladění ve smíšeném režimu s předchozími verzemi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] se nepodporuje.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Upgrade [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] na verzi 2.0, 3.0, 3.5 nebo 4.0.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)