---
title: 'Chyba: Nelze se připojit k názvu počítače &lt; &gt; . Počítač se v síti nepodařilo najít. | Dokumentace Microsoftu'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd1402a476ce2dceaaaf78580b36db20c3eed24f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682561"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Chyba: Nelze se připojit k názvu počítače &lt; &gt; . Počítač se v síti nepodařilo najít.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K tomuto chování dochází, pokud je splněna jedna z následujících podmínek:  
  
- Připojení ke vzdálenému počítači bylo přerušeno.  
  
- Váš uživatelský účet na vzdáleném počítači je zakázán.  
  
- Platnost vašeho hesla na vzdáleném počítači vypršela.  
  
### <a name="to-resolve-this-behavior"></a>Řešení tohoto chování  
  
- Ujistěte se, že je místní počítač a vzdálený počítač ve stejné síti. K tomu použijte Průzkumníka Windows (nebo Průzkumníka souborů) a pokuste se získat přístup ke vzdálenému počítači.  
  
     ani  
  
- Ujistěte se, že uživatelský účet, který používáte pro připojení ke vzdálenému počítači, je povolený.  
  
     ani  
  
- Ujistěte se, že heslo, které používáte pro připojení ke vzdálenému počítači, je platné a nevypršela jeho platnost.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
