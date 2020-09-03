---
title: Dodavatelé portů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153709"
---
# <a name="port-suppliers"></a>Dodavatelé portů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V souvislosti s architekturou ladicího programu, **dodavatelem portu**:  
  
- Je součástí serveru a poskytuje porty na vyžádání daného serveru.  
  
- Může přidat nebo odebrat porty z nadřazeného serveru.  
  
- Může vytvořit výčet všech portů, které daný server dodal.  
  
- Je reprezentován rozhraním [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , které je zaregistrováno v aplikaci Visual Studio prostřednictvím registru. Toto rozhraní lze získat voláním [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje výchozího dodavatele portu a výchozí port. Pokud je nutné implementovat vlastní port, musí být také implementován vlastní dodavatel portu, aby tyto vlastní porty poskytoval.  
  
## <a name="see-also"></a>Viz také  
 [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Přístavu](../../extensibility/debugger/ports.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
