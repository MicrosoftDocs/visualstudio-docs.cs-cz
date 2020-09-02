---
title: Problémy se zabezpečením | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704424"
---
# <a name="security-issues"></a>Problémy se zabezpečením
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chcete-li ladit program pomocí sady Visual Studio, jsou jediná potřebná oprávnění stejná jako vývojář, který potřebuje spustit program. To zahrnuje vzdálené ladění ve většině případů (některé situace zahrnující jiné služby, jako je třeba Internetová informační služba) může vyžadovat vyšší úroveň oprávnění.  
  
 I když je spuštěná aplikace Visual Studio, sleduje správce ladění procesů (PDM) procesy ladění na místním počítači. Vzdáleně je program s názvem msvsmon.exe spuštěn vývojářem, který zpracovává vzdálené ladění a zpřístupňuje PDM. (Všimněte si, že msvsmon.exe není služba a je nutné ji spustit ručně, aby se na tomto počítači povolilo vzdálené ladění.) Pokud není spuštěna aplikace Visual Studio (nebo msvsmon.exe), nejsou sledovány žádné procesy pro ladění.  
  
 To znamená, že vývojář může ladit programy, které zahájily bez zvláštních oprávnění. Vývojář může dokonce ladit procesy zahájené někým jiným, pokud je tato jiná osoba členem stejné skupiny zabezpečení. Aby bylo možné povolit vzdálené ladění, je nutné pouze zkopírovat potřebné soubory do vzdáleného počítače a spustit msvsmon.exe (Další informace najdete v tématu [Nastavení vzdálených nástrojů na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) ).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)   
 [Správce ladění procesů](../../extensibility/debugger/process-debug-manager.md)   
 [Nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
