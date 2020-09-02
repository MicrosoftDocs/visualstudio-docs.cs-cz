---
title: Registrace vlastního ladicího modulu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703607"
---
# <a name="registering-a-custom-debug-engine"></a>Registrace vlastního ladicího stroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí stroj se musí zaregistrovat jako továrna tříd podle konvencí COM a také registrovat v aplikaci Visual Studio prostřednictvím podklíče registru sady Visual Studio.  
  
> [!NOTE]
> Příklad, jak registrovat ladicí stroj, najdete v ukázce TextInterpreter, který je sestaven jako součást [kurzu: sestavení ladicího stroje pomocí ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proces serveru DLL  
 Ladicí stroj se obvykle implementuje ve vlastní knihovně DLL jako server COM. To znamená, že ladicí stroj musí zaregistrovat identifikátor CLSID svého objektu pro vytváření tříd pomocí modelu COM, aby k němu mohl přistupovat aplikace Visual Studio. Ladicí stroj se pak musí sám zaregistrovat společně se sadou Visual Studio, aby bylo možné vytvořit jakékoli vlastnosti (jinak označované jako metriky) ladicí stroj podporuje. Volba metrik, která je zapsána do podklíče registru sady Visual Studio pro modul ladění, závisí na funkcích, které ladicí stroj podporuje.  
  
 [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) popisuje nejen umístění registru potřebná k registraci ladicího stroje. Popisuje také knihovnu dbgmetric. lib, která obsahuje řadu užitečných funkcí a deklarací pro vývojáře v jazyce C++, které usnadňují práci s registrem.  
  
### <a name="example"></a>Příklad  
 Následuje typický příklad (z ukázky TextInterpreter), který ukazuje, jak používat `SetMetric` funkci (z dbgmetric. lib) k registraci ladicího stroje se sadou Visual Studio. Předávané metriky jsou také definovány v dbgmetric. lib.  
  
> [!NOTE]
> TextInterpreter je základní ladicí stroj; neimplementuje – a proto se neregistruje – žádné další funkce. Ucelený ladicí stroj by měl celý seznam `SetMetric` volání nebo jejich ekvivalent, jeden pro každou funkci, kterou ladicí stroj podporuje.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Kurz: sestavení ladicího stroje pomocí ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
