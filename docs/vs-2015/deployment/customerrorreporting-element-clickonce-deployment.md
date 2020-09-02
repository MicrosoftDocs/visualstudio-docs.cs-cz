---
title: '&lt;customErrorReporting – &gt; element (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7e8a0db3e10a277fe1c4a2f8fcd2bb85fa69e69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187834"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting – &gt; element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje identifikátor URI, který se má zobrazit, když dojde k chybě.  
  
## <a name="syntax"></a>Syntax  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento element je volitelný. Bez něho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zobrazuje dialogové okno chyby zobrazující zásobník výjimky. Pokud `customErrorReporting` je prvek přítomen, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] místo toho zobrazí identifikátor URI, který je označen `uri` parametrem. Cílový identifikátor URI bude obsahovat třídu vnější výjimky, třídu vnitřní výjimky a zprávu vnitřní výjimky jako parametry.  
  
 Tento prvek použijte k přidání funkce zasílání zpráv o chybách do aplikace. Vzhledem k tomu, že vygenerovaný identifikátor URI obsahuje informace o typu chyby, může váš web analyzovat tyto informace a zobrazovat, například příslušnou obrazovku pro řešení problémů.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje `customErrorReporting` element spolu s generovaným identifikátorem URI, který může vytvořit.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
