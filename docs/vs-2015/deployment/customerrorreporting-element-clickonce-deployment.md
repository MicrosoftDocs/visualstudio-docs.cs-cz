---
title: '&lt;customErrorReporting&gt; – Element (nasazení ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: cf4a723fe5986287859134d0f97868a19956f5a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252015"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; – Element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje identifikátor URI, chcete-li zobrazit, když dojde k chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento element je volitelný. Bez něho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zobrazí dialogové okno chyby zobrazující zásobník výjimek. Pokud `customErrorReporting` element je k dispozici, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] místo toho zobrazí identifikátor URI indikován `uri` parametru. Cílový identifikátor URI bude obsahovat třídy vnější výjimky, vnitřní výjimka třídy a zpráva o vnitřní výjimce jako parametry.  
  
 Tento element slouží k přidání zpráv o chybách funkce do vaší aplikace. Vzhledem k tomu, že vygenerovaný identifikátor URI obsahuje informace o typu chyby, vaše webová stránka může analyzovat a zobrazit, například obrazovku řešení potíží tyto informace.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje `customErrorReporting` element spolu s vygenerovaný identifikátor URI může vrátit.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)



