---
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3acc40e2b906bd46b832d9fa11578de346014042
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787768"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá název relace, která provádí ladění tohoto procesu. Integrované vývojové prostředí (IDE) může tyto informace zobrazit uživateli, který ladí konkrétní proces na konkrétním počítači.  
  
> [!NOTE]
> Tato metoda je zastaralá a její implementace by měla vždycky vracet `E_NOTIMPL` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda by měla vždycky vracet `E_NOTIMPL` .  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
