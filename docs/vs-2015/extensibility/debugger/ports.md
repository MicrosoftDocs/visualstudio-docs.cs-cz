---
title: Porty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153689"
---
# <a name="ports"></a>Porty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V rámci architektury ladicího programu **port**:  
  
- Je kontejner pro sadu procesů spuštěných na serveru. Port může například představovat připojení k systém Windows CE zařízení na základě sériového kabelu nebo k síťovému počítači, který není typu DCOM. Jeden speciální port nazvaný místní port obsahuje všechny procesy spuštěné v místním počítači.  
  
- Může identifikovat podle názvu nebo identifikátoru.  
  
- Může vytvořit výčet všech procesů spuštěných na portu a spustit a ukončit tyto procesy.  
  
- Je reprezentován rozhraním [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , které je vytvořeno předáním argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje výchozí port, který zpracovává všechny procesy, nativní a spravované procesy založené na systému Windows. Pro připojení k externím zařízením, která nejsou založená na systému Windows, musí být implementován vlastní port. Aby bylo možné tyto vlastní porty poskytovat, musí být také implementován vlastní dodavatel portu.  
  
## <a name="see-also"></a>Viz také  
 [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesem](../../extensibility/debugger/processes.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
