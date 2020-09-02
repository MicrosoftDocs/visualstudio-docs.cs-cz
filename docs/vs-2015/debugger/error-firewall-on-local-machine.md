---
title: 'Chyba: Brána firewall v místním počítači | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35ccc65e7aa19c830603d62254385d289a8477ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697416"
---
# <a name="error-firewall-on-local-machine"></a>Chyba: Brána firewall v místním počítači
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Brána firewall pro připojení k Internetu v místním počítači, ze kterého se spouští sada Visual Studio, není nastavená tak, aby povolovala vzdálené ladění. Pro spravované nebo nativní vzdálené ladění s výchozím přenosem musí být port TCP 135 otevřený pro přenosy modelu DCOM. Sdílení souborů a tiskáren musí být otevřené a devenv.exe musí být přidány do seznamu výjimek. Otevírání některých portů IPSEC může být také nutné.  
  
 Další informace najdete v tématu [nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
