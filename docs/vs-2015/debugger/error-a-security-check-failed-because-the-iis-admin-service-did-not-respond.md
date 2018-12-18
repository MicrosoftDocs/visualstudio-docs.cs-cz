---
title: 'Chyba: Kontrola zabezpečení selhala, protože služba správy služby IIS neodpověděla. | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6215648cba97e17ab143538afb4936a480adae4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769022"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Chyba: Kontrola zabezpečení selhala, protože služba správy služby IIS neodpověděla.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chyba nastane, pokud správce služby IIS neodpovídá. To obvykle znamená, že dojde k problému s instalací služby IIS. Nejprve ověří, zda je spuštěna služba pomocí **služby** nástroj z **nástroje pro správu**.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Znovu nainstalujte IIS pomocí **přidat nebo odebrat programy** ovládacích panelech.  
  
-   -nebo-  
  
-   Služba IIS odeberte z počítače, pomocí ovládacího panelu Přidat nebo odebrat programy. Pokud jste odebrali službu IIS a stále máte problémy, zkontrolujte registru a ujistěte se, že tento klíč už existuje:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     -nebo-  
  
-   Zakážete službu Správce služby IIS pomocí nástroje pro správu ovládacích panelů. Tato akce zakáže služby IIS na vašem počítači.  
  
     Po provedení některé z těchto tří kroků, restartujte počítač.  
  
     Další informace najdete v dokumentaci služby IIS.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



