---
title: Kontext dokumentu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3034c9ca02fca8e91eb1aa5e4d0eb5a2fe1f773f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200586"
---
# <a name="document-context"></a>Kontext dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění, **kontext dokumentu**:  
  
- Představuje pozici ve zdrojovém souboru. V případě jazyků, kde zdrojový soubor nemusí být k dispozici, určuje kontext dokumentu pozici v dokumentu obvykle generované běhovým prostředím. Skriptovací stroj může například vygenerovat dokument ze skriptu. Další informace najdete v tématu [pozice dokumentu](../../extensibility/debugger/document-position.md).  
  
- Popisuje pozici ve zdrojovém dokumentu, která odpovídá kontextu kódu. Obslužná rutina symbolu mapuje kontext kódu k dokumentaci v kontextu pomocí informací generovaných kompilátorem nebo překladačem.  
  
- Je implementováno pomocí rozhraní [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  
  
## <a name="see-also"></a>Viz také  
 [Kontext kódu](../../extensibility/debugger/code-context.md)   
 [Zprostředkovatel symbolů](../../extensibility/debugger/symbol-provider.md)   
 [Rozhraní poskytovatele symbolů](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
