---
title: 'Chyba: ladění ve smíšeném režimu pro procesy x64 je podporováno pouze v případě, že používáte Microsoft .NET Framework 4 nebo vyšší | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190a6e890ce31ce2aa66ff474bb9e4b1976a6c46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824001"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Chyba: Ladění ve smíšeném režimu pro procesy x64 je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 4 nebo vyšší.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li ladit smíšený nativní a spravovaný kód v 64m procesu, je nutné mít [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi 4. Ladění ve smíšeném režimu s 64 procesy s [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzemi staršími než 4 se nepodporuje.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Proveďte jeden z následujících kroků:  
  
  - Upgradujte [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] na verzi 4.  

  - Sestavte 32 verzi vaší aplikace pro ladění.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
